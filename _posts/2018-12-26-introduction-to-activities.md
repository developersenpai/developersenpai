---
layout: post
title: "A Full and Comprehensive Style Test"
description: "Test post for style"
date: 2016-08-15
tags: test, style
comments: true
---

## Introduction to Activities | Developer Senpai

Unlike programming paradigms in
which apps are launched with a `main()` method, the Android
system initiates code in an `Activity` instance by
invoking specific callback methods that correspond to specific stages of
its lifecycle.

[Intent filters](https://developer.android.com/guide/components/intents-filters.html)
are a very powerful feature of the Android platform. They
provide the ability to launch an activity based not only on an
*explicit* request, but also an *implicit* one. For example,
an explicit request might tell the system to “Start the Send Email activity
in the Gmail app". By contrast, an implicit request tells the
system to “Start a Send Email screen in any
activity that can do the job." When the system UI asks a user which app to use
in performing a task, that’s an intent filter at work.

## Managing the activity lifecycle

**onCreate()**

For example, your app should create views and bind data to lists here. Most importantly, this is where you must call `setContentView()` to define the layout for the activity's user interface. When `onCreate()` finishes, the next callback is always `onStart()`. 

**onStart()**

As `onCreate()` exits, the activity enters the Started state, and the activity becomes visible to the user. This callback contains what amounts to the activity’s final preparations for coming to the foreground and becoming interactive. 

**onResume()**

The system invokes this callback just before the activity starts interacting with the user. At this point, the activity is at the top of the activity stack, and captures all user input. Most of an app’s core functionality is implemented in the `onResume()` method. 

The `onPause()` callback always follows `onResume()`. 

**onPause**

 The system calls `onPause()` when the activity loses focus and enters a Paused state. This state occurs when, for example, the user taps the Back or Recents button. When the system calls `onPause()` for your activity, it technically means your activity is still partially visible, but most often is an indication that the user is leaving the activity, and the activity will soon enter the Stopped or Resumed state. 

 An activity in the Paused state may continue to update the UI if the user is expecting the UI to update. Examples of such an activity include one showing a navigation map screen or a media player playing. Even if such activities lose focus, the user expects their UI to continue updating. 

 You should **not** use `onPause()` to save application or user data, make network calls, or execute database transactions. For information about saving data, see [ Saving and restoring activity state](https://developer.android.com/guide/components/activities/activity-lifecycle.html#saras). 

 Once `onPause()` finishes executing, the next callback is either `onStop()` or `onResume()`, depending on what happens after the activity enters the Paused state. 

**onStop()**

The system calls `onStop()` when the activity is no longer visible to the user. This may happen because the activity is being destroyed, a new activity is starting, or an existing activity is entering a Resumed state and is covering the stopped activity. In all of these cases, the stopped activity is no longer visible at all. 

The next callback that the system calls is either `onRestart()`, if the activity is coming back to interact with the user, or by `onDestroy()` if this activity is completely terminating. 

**onRestart()**

The system invokes this callback when an activity in the Stopped state is about to restart. `onRestart()` restores the state of the activity from the time that it was stopped. 

This callback is always followed by `onStart()`. 

**onDestroy()**

The system invokes this callback before an activity is destroyed. 

This callback is the final one that the activity receives. `onDestroy()` is usually implemented to ensure that all of an activity’s resources are released when the activity, or the process containing it, is destroyed. 
