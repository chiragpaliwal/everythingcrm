---
layout: post
title:  "Inject dependencies in JavaScript Web Resource"
description: Microsoft released a new feature on JavaScript Web Resource in Dynamics 365. Now, you would be able to inject dependencies in JavaScript web resources
author: piyush
categories: [ dynamics-365 ]
---
Microsoft gave a breather to all the developers who work on JavaScript Web Resource in Dynamics 365 with the release of version 9.0. Now, you would be able to inject dependencies in JavaScript web resources.

Consider a scenario where you have created a field which has no business significance, however you require that field for some calculations that are being done on the form. In previous versions of CRM, we used to do this by having a hidden tab in our form and placing all these fields so that they can be accessed in our code. If the field is not present on the form, then your JavaScript code that references this field would fail or not execute as per your expectations. 

To overcome this issue, we can now put dependencies while setting up JavaScript web resources. Let’s start building one.

I have created a whole number field in Account entity called as `Age` or `Account Age`. This value needs to be output when someone clicks a button or changes some value in any other field (triggers could be anything, ultimately you should grasp the concept here), in my case it is on change of Account Name field. 

Following is the JavaScript code that we need to fire when someone changes the Account Name.

```javascript
// JavaScript source code
function DisplayAge(executionContext) {
    var formCtx = executionContext.getFormContext();
    if (formCtx.getAttribute("winf_age") !== null) {
        Xrm.Navigation.openAlertDialog({ text: "Account Age: " + formCtx.getAttribute("winf_age").getValue() });
    } else {
        Xrm.Navigation.openAlertDialog({ text: "Age field does not exist on the Form" });
    }
}
```
Notice that in this code, I am retrieving the value from `Age` field, now naturally we will be required to place this field on the form, right? No, that’s wrong, that’s where injecting dependencies will come in picture. While creating the web resource, there would be a new tab called as `Dependencies`.

![JavaScript Web Resource dependency injection screen](/assets/images/Dependencies_JavaScript_WebResource.webp "JavaScript Web Resource dependency injection screen")

You have the following options available with you

* Add a dependent Web Resource
* Add an entity and the attribute name which are dependent on this script.
  * The beauty is that if this script is a common one and a lot of other entities are also using it then you can define all those entities and attributes here.

## What happens when this script loads?
Now, I just added the dependency and published all my changes, notice that we have not put this field on Account form yet. It should still give you the result and output the value of Age.

![Age field value is output based on the script we wrote above](/assets/images/Age-field-output.webp "Age field value is output based on the script we wrote above")

And boom! it just works! Now, lets try to remove this dependency and see what changes.

![Script output after removal of age field from JavaScript web resource dependency](/assets/images/Age-field-error.webp "Script output after removal of age field from JavaScript web resource dependency")

So there we have it, no more hidden fields on the form.

## What are the benefits we get from it?
* No need for putting unnecessary fields on the form just because one script needs it.
* No unexpected script failures as the system will always ensure that the value of this field is available for your script to use.
* System Customizers will be given a warning when they try to delete this field, which happens all the time and results in script failures.

![Age field dependencies](/assets/images/ShowDependencies.webp "Age field dependencies")

So, there you have it, everything you need to know about JavaScript Web Resource dependencies. Happy CRMing!