---
layout: post
title:  "Manage multiple Office 365 domain logins like a pro!"
description: Microsoft released a new feature on JavaScript Web Resource in Dynamics 365. Now, you would be able to inject dependencies in JavaScript web resources
author: piyush
categories: [ dynamics-365 ]
tags: productivity
---
If you are an administrator handling multiple Office 365 domains then I am sure you would have come across the problem of not being able to easily switch between domains and perform basic administrative tasks.

## But I can use Multiple Browsers, right?
Yes, of course, you can use multiple browsers but don’t you think it is kind of an overkill having to install 4-5 different types of browsers just to perform some task on a website. This idea doesn’t make any sense and I love using chrome and would like this functionality to be working on it. 

## Alright, then why not Incognito Mode?
Sure, using chrome along with Incognito mode works, but again it limits you to only 2 Office 365 accounts. You can run one in the normal mode and open up another in Incognito mode.

## The biggest pain with approaches mentioned above
The two methods mentioned above would definitely work out for most of the folks because a normal person would not be having more than 2 Office 365 domains.

Over the period of time, you would soon realize that it is a pain to provide credentials every single time you open your browser and to add to it is the Two-Factor Authentication which expects you to provide the OTP/Code, etc.

So, what do we do.

## Google Chrome Profiles
There is a very neat feature available inside chrome which allows users to create multiple profiles. All you have to do is on the top right corner of the chrome window, click the user icon and select Manage People.

![Manage People](/assets/images/Manage_People.png "Manage People")

This will open up a new window which will show all the user profiles that are available on the system. This is where you will have an option to Add Person.

> The idea here is simple, one person equals one Office 365 account

So, if I have 3 Office 365 domains to manage then I will create 3 Persons in chrome.

![Add Person's window in Chrome](/assets/images/Add_Persons_Window_Chrome.png "Add Person's window in Chrome")

The next thing you need to do is open up each of these profiles you just created and login to that particular Office 365 account and ensure you tick the option that says Stay logged in and you are done. The next time you open this profile, Chrome will know which account to open up for you.

![Switch Profiles in Chrome](/assets/images/Profile_Switcher.png "Switch Profiles in Chrome")

> The additional benefit here is that you don’t need to Login ever. Just open the right profile and you are good to go