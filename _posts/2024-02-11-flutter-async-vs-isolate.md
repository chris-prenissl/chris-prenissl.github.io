---
title: "Developing for Flutter as an Android Developer"
date: 2024-02-18 18:00:00 +0100
categories: [Flutter]
tags: [flutter, development, programming]
---

Somehow I had a bad feeling before developing mobile apps with **Flutter**.
As a software developer I came across different languages and felt just at home with Kotlin for Android.
Flutter uses yet another programming language and in the past non-native cross-platform Frameworks had a bad reputation.

This article is about how Flutter with Dart surprised me, how it is different/similar to Android
 and what I learned in the last couple of months.

## Dart - Another programming language
There are many well established programming languages. So why did the Flutter Team to decide to use just another one?
In the official _[Flutter FAQ](https://docs.flutter.dev/resources/faq#why-did-flutter-choose-to-use-dart)_ they state 
that several reasons like "Fast allocations", "Predictable, high performance" and "Object-orientation" helped to decide
for Dart as the main language, but the main reasons were probably the *JIT* (Just-In-Time compiler) with the possibility
to instantly reload the page or app on device after a code change, and the Ahead-Of-Time compiler.

The first thing I instantly liked was the JIT features like *Hot Reload* for loading code changes and reloading 
the current state and *Hot Restart* is the same as Hot Reload but restarts the app and therefore lose the app's state.
The deployment to the *Dart VM* which is used to run the Flutter code takes much less time than recompiling native code.
Since Flutter also can use native code, there is a reason to recompile native code and redeploy the app at certain point.
You can also find other cases where the *Hot Reload* / *Hot Restart* won't succeed under 
_[Hot Reload](https://docs.flutter.dev/tools/hot-reload)_.

As a Kotlin Developer it didn't take much time to understand the language features and syntax of *Dart*. Some parts like 
double colons at the end of the line and function declarations felt like C/C++. Other parts like dynamic types and extensions
are not so much of a difference to Kotlin. 
Even when you get lost, the documentation and guides of the Flutter team are very helpful. There is basically a guide for
every type of programmer who is new to Flutter, so there is also a 
[Guide for Android Developer](https://docs.flutter.dev/get-started/flutter-for/android-devs)_, so you can translate your knowledge
from other languages faster.

## UI - Everything is a Widget until not
If you are familiar to declarative frameworks like *Swift UI* or *Jetpack Compose* than you should have a quick start
with the *Widget* Structure of Flutter code. 

Most UI elements of a Flutter app are nested Widgets. A so called *Widget Tree* defines the Layout, painting of the canvas and
user interactions are handled. In the _[Widget Catalog](https://docs.flutter.dev/ui/widgets)_ you can find a widget for your use-case.

There are two kinds of Widgets in Flutter (_[Widget](https://api.flutter.dev/flutter/widgets/Widget-class.html)_):
When a widget won't change or should not control the state itself, you can use a *StatelessWidget*.
When you want to manage state changes of your UI you can use a *StatefulWidget*.
Setting a state within a *StatefulWidget* is as easy as to call *setState* in a UI method.

You not only declare UI in your Widget but also provide dependencies like repositories or models with the *BLoC* package, 
settings or navigation routes. Most of the time you can consume these configurations via the context parameter in the 
current Widget.

## MVVM Design

## Concurrency and Threading - Future and Isolates

## Final thoughts