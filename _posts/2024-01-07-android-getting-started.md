---
title: "Getting started with Android Development"
date: 2024-01-08 11:19:00 +0100
categories: [Android]
tags: [android, guide, learning, setup, programming]
---

A lot has changed in the world of Android Development. This guide helps you get started with setting up 
the Coding Environment, write your first apps and keep you engaged for mastering your skills and prepare you for
the professional life as an Android Developer. Think of this article as the entrypoint for beginners or experienced
developers that switching or coming back to Android.

_If you want to create your own Android System or dig into
the Android Operating System please refer to [Android Open Source Project](https://source.android.com)_.

## Motivation
The Android Operating System exists quite a long time. Apple released
the first iPhone in 2007 but Google acquired Android in 2005 and established
the system as a competitor _([The history of Android](https://www.androidauthority.com/history-android-os-name-789433/))_.
Since then the Android system gained traction with many updates and
is still evolving.

The market share for Android still beats the only competitor Apple.

![Market Share Mobile Operating Systems](https://chris-prenissl.github.io/assets/img/2024-01-7-android-getting-started/StatCounter-os_combined-ww-monthly-202212-202312-2.png){: w="700" h="400" }

__Market Share of Mobile Operating Systems (https://gs.statcounter.com/os-market-share/mobile/worldwide)__

Also there are a variety of Devices that can run Android: Besides the large Smartphone sector Android can be found on Fridges, TVs, Smartwatches, Chromebooks,
and will be established soon as Standalone System in the car _([What is Android Automotive?](https://www.forbes.com/wheels/features/what-is-android-automotive/))_.

Even though there are many cross platform solutions to develop for Android and iOS like Flutter, React Native, Cordova or Ionic, there is a need for
"native" Android Developers (By "native" I refer to creating code which directly compiles for the JVM on the Android System). 
Here are several reasons for nativeAndroid Development:

- _Performance_: Native code is faster and more memory efficient.
- _Hardware Access_: For accessing specific sensors or other hardware near abstractions native code is best suited.
- _Access to newest Features_: Android Studio has the latest updates before cross platform tools adopt them.
- _Cross Platform_: When you understand native Android you are prepared for cross platform development.

Additionally, Jetbrains (the Company behind Kotlin, the main programming language of Android Development) has also established
its own Cross-Platform framework _Kotlin Multiplatform_, which uses Kotlin and all the tools and important frameworks well known to Android 
to also develope iOS, Web, Linux, Windows and Mac applications _([Kotlin Multiplatform](https://kotlinlang.org/docs/multiplatform.html))_. 

## Technical Requirements
The most technical expensive tool for Android Development would be _Android Studio_ but with a modern operating 
system (at least Windows 8, MacOS 10.14 or Linux 64bit) with at least 8 GB RAM you should be fine.

## Tools
The good thing is, that you only need one suite of tools and that is _Android Studio_. This IDE (Integrated Development Environment) serves
all the tools like the _JDK_ (Java Development Kit), _Gradle_ (build tool), _Android Emulator_ (Virtualisation of an Android Device) and
several debugging and syntax highlighting tools.
It is the most important industry standard IDE, but you could use _Intellij_ or any other text editor if you want to have it harder than it needs to be.

### Installing Android Studio
This part is easy. Just follow [Install Android Studio](https://developer.android.com/studio/install) for your system.
If you want to test the newest features you can install the _Canary build_ or the _Beta build_ (more stable than Canary)
[preview release](https://developer.android.com/studio/preview).

> Preview releases should be carefully considered since they are not stable yet (_Beta build_) or the features 
> are in an experimental state.
{: .prompt-warning }

### Installing Git
_Git_ is the leading version control system in Software Development.
If you are on Mac or on Linux then you can skip this part, since it is already installed.

For Windows you can install _Git_ via [Download for Windows](https://git-scm.com/download/win). Make sure 
you choose the right version matching your Windows system.

## Helpful Guides
The best thing about starting Android Development is that there is a large community of developers that are happy to help.
Because there are many documentations, guides and tutorials out there, it is also easy to get lost on where to start. 

### First Steps
The best way to start your development journey is by taking the official course
[Android Basics with Compose](https://developer.android.com/courses/android-basics-compose/course) from Google.
It covers the central topics like creating your first app, building UI with the new established framework Compose,
learning Kotlin as the main programming language for Android, accessing the Internet and managing SQL databases. 
These code labs also aid you with the Android documentation.

### Next Steps
There are several guides that can help you harness your skills:

- _[Philipp Lackner](https://www.youtube.com/@PhilippLackner)_: Especially his short technical videos can solve a lot of errors,
but he has also many courses for developing apps with industry standard architecture. 
- _[Android Developer courses](https://developer.android.com/courses)_: There are many other courses that help you with specific use cases.
- _[ADB tutorial](https://www.youtube.com/watch?v=uOPcUjVl2YQ)_: Entry point when you want to read out your Android System
- _[Gradle](https://www.youtube.com/watch?v=-dtcEMLNmn0)_: This helps you to prevent a lot of headaches on build errors.

## Most important resources
- _[Documentation](https://developer.android.com/docs/)_: You should familiarize with the logic and structure of the official docs so you understand
how your code works in the frameworks so you can help yourself with a lot of issues.
- _[Material IO](https://m3.material.io)_: Google's page for guidelines on industry standard UI design which is also included in many frameworks.
- _[Kotlin Documentation](https://kotlinlang.org/docs/home.html)_: Every feature related to the Language itself on which Android is based of.
- _[Kotlin Playground](https://play.kotlinlang.org/)_: You can always play with code on Jetbrains official playground.
- _[Android Code Search](https://cs.android.com)_: Sometimes you need to have a deeper understanding on how the Android OS works, therefore 
this handy platform helps you quickly find and understand the source code of the OS.

## Keeping up to date with the Android World
There are several channels that bring you news for Android:
- _[Android Developers Blog](https://android-developers.googleblog.com)_: Keep up to date with the official blog from Android Developers.
- _[Android Developers Backstage](https://adbackstage.libsyn.com)_: Developers of the most influential frameworks talk about their journey.
This helps with deeper understanding.
- _[Material Blog](https://material.io/blog/)_: Important resource on everything what is new in the UI world of Android.
- _[Android Dev Discord](https://discord.gg/S2QWCxpr9C)_: Discord Channel with a lot of Android devs.
- _[Philipp Lackner](https://www.youtube.com/@PhilippLackner)_: When a new important framework is released it is likely he will cover it.

## A great Start
This guide is just a beginning and is not complete, but it should give you a good entrypoint and have important resources for when you get stuck.
Please feel free to contact me if something is missing, you want to get help or discuss Android topics:)

Have a great start with Android!