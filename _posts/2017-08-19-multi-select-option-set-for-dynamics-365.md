---
layout: post
title:  "Multi-select option set for Dynamics 365"
description: The most awaited feature of Dynamics 365 is here, multi-select option set. Lets find out everything we need to know about it and try to configure one
author: piyush
categories: [ dynamics-365 ]
image: assets/images/multi-select.jpg
tags: featured
---
The most awaited and appreciated features of Dynamics 365 is finally here; *drumroll* Introduction of multi-select option sets.
I remember searching for a solution back in 2011 with CRM 4.0, and since then it has been a very long wait. Ok, so let’s get started and take a look at the implementation and see how best we can leverage it.

## What is multi-select option set and why should I care?
Well, as the name goes; this control allows you to select multiple values, it was a major setback previously when for a straightforward functionality like tagging an account or any other record with values like,`Top-25` `Top-10` etc. was only possible by creating an additional entity and referencing its records by building multiple relationships. While it had it’s own plus and minus but this solution was not really liked by many thereby generating a strong need of feature like this.

## Scenario
Continuing from the above example, this is what we want to achieve; We should be able to tag an account record with one or more tags like `Top-25`, `Top-10`, `Top-100`, `Improve Relationship`

## Create a multi-select option set
Creating an option set is very simple, and you would have done it multiple times via customization. Let’s start there.
Go to **Account** entity and **Create a new field** in it and let’s name it **Tags**.

![Multi select option set field creation](/assets/images/Multi-select-option-set-field-creation.png "Multi select option set field creation")

Notice in the image above there is a new data-type called MultiSelect Option Set, rest everything is pretty much the same as creating any other option-set. 

For our example, I have added the necessary options with relevant colors and added this newly created field on Account form. Take a look at the screenshot.

![Multi select option set display](/assets/images/Multi-select-option-set-display.png "Multi select option set display")

You can select multiple values now and save the record like usual. It’s that simple.

> Oh btw, you can also start typing the options here as it supports auto-complete

## Search via advanced find
Searching for a specific value in a multi-select option set is very simple and pretty straight-forward; just the way you would select multiple values for a lookup field. Here, take a look.

![Multi select option set advanced find](/assets/images/Multi-select-option-set-advanced-find.png "Multi select option set advanced find")

## Ok, I got it but what about programmability?
Its is the best part. MultiSelect Option set primarily supports all the client APIs that are available for standard option sets.

A quick list of functions that are available. Click an option, and it will take you to it’s respective MSDN page

## OptionSet Attribute Client APIs
* [getInitialValue](https://msdn.microsoft.com/en-us/library/gg334409.aspx#BKMK_getInitialValue)
* [getOption](https://msdn.microsoft.com/en-us/library/gg334409.aspx#BKMK_getOption)
* [getOptions](https://msdn.microsoft.com/en-us/library/gg334409.aspx#BKMK_getOptions)
* [getSelectedOption](https://msdn.microsoft.com/en-us/library/gg334409.aspx#BKMK_getSelectedOption)
* [getText](https://msdn.microsoft.com/en-us/library/gg334409.aspx#BKMK_getText)

## OptionSet Control Client APIs
* [addOption](https://msdn.microsoft.com/en-us/library/gg334266.aspx#BKMK_addOption)
* [clearOptions](https://msdn.microsoft.com/en-us/library/gg334266.aspx#BKMK_clearOptions)
* [removeOption](https://msdn.microsoft.com/en-us/library/gg334266.aspx#BKMK_removeOption)

> The only difference from normal option set here would be that some of the methods mentioned above would return an array instead of a single value.

## Alright, anything else that I should be aware?
* They are currently available only for [Unified Interface]({% post_url 2017-08-15-lets-explore-unified-interface-for-dynamics-365-or-crm %}) and web client.
* Following form types are supported
  * Main
  * Quick Create
  * Quick view
* No legacy forms support.
* You can send integer values of the option set as query string parameter while opening up a create record form to set its value.

So, that’s it for now. I think all the areas of this neat feature are covered. Please let me know in the comments below if you think I may have missed something.