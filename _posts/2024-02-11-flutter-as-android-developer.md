---
title: "Developing for Flutter as an Android Developer"
date: 2024-02-18 18:00:00 +0100
categories: [Flutter]
tags: [flutter, development, programming]
---

Somehow I had a bad feeling before developing mobile apps with **Flutter**.
As a software developer I came across different languages and felt just at home with Kotlin for Android.
Flutter uses yet another programming language and in the past non-native cross-platform frameworks had a bad reputation.

This article is about how Flutter with Dart surprised me, how it is different/similar to Android
and what I learned in the last couple of months.

## Dart - Another programming language
There are many well established programming languages. So why did the Flutter Team to decide to use another one?
In the official _[Flutter FAQ](https://docs.flutter.dev/resources/faq#why-did-flutter-choose-to-use-dart)_ they state 
that several reasons like "Fast allocations", "Predictable, high performance" and "Object-orientation" helped to decide
for Dart as the main language, but the main reasons were probably the *JIT* (Just-In-Time compiler) with the possibility
to instantly reload the current view or the app on device after code change, and the Ahead-Of-Time compiler.

The first thing I instantly liked was the JIT features like *Hot Reload* for loading code changes and reloading 
the current state and *Hot Restart*, which is the same as Hot Reload but restarts the app and therefore the app's state is lost.
The deployment to the *Dart VM* which is used to run the Flutter code takes much less time than recompiling native code.
Since Flutter also can use native code, there is a reason to recompile native code and redeploy the app when changed.
You can also find other cases where the *Hot Reload* / *Hot Restart* won't succeed under 
_[Hot Reload](https://docs.flutter.dev/tools/hot-reload)_.

As a Kotlin Developer it didn't take much time to understand the language features and syntax of *Dart*. Some parts like 
double colons at the end of the line and function declarations felt like C/C++. Other parts like dynamic types and extensions
are not so much different to Kotlin. 
Even when you get lost, the documentation and guides of the Flutter team are very helpful. There is basically a guide for
every type of programmer who is new to Flutter, so there is also a 
[Guide for Android Developer](https://docs.flutter.dev/get-started/flutter-for/android-devs)_ and other backgrounds, so you can 
translate your knowledge from other languages much faster.

## UI - Everything is a Widget (until it's not)
If you are familiar to declarative frameworks like *Swift UI* or *Jetpack Compose* than you should have a quick start
with the *Widget* Structure of Flutter code. 

Most UI elements of a Flutter app are nested Widgets. A so called *Widget Tree* defines the Layout, painting of the canvas and
how user interactions are handled. In the _[Widget Catalog](https://docs.flutter.dev/ui/widgets)_ you can find a widget for your use-case.

There are two kinds of Widgets in Flutter (_[Widget](https://api.flutter.dev/flutter/widgets/Widget-class.html)_):
When a widget won't change or should not control the state itself, you can use a *StatelessWidget*.
When you want Flutter to manage state changes of your UI you can use a *StatefulWidget*.
Setting a state within a *StatefulWidget* is as easy as to call *setState* in a UI method.

You not only declare UI in your Widget but also provide dependencies like repositories or models for example with the famous *BLoC* 
package. Settings or navigation routes can also be provided within widgets. Most of the time you can consume these configurations 
via the context parameter in the current Widget. All of this seems similar to Jetpack Compose on Android, but when it comes to layouting,
there are some differences. You would use modifiers in Compose to control part of your layout, when for most cases in Flutter you would
use another Widget as parent of your content Widget. E.g. in Compose you would use a modifier to control padding, where in Flutter you 
would wrap your Widget with another Widget Padding.

Example:
```Dart
void main() => runApp(const MyApp());

class MyApp extends StatelessWidget {
  const MyApp({super.key});

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      home: Scaffold(
        appBar: AppBar(
          title: const Text('My Home Page'),
        ),
        body: Padding(
          child: Text('Hello Flutter')
        ),
      ),
    );
  }
}
```

As described in
_[Architectural Overview - Widgets](https://docs.flutter.dev/resources/architectural-overview#widgets)_ the code for UI
should not contain side effects since it could potentially be called each frame.

So *Widgets* are basically classes that contain code for composing the UI (with passing references) and should be designed for 
fast execution. Different logic should be handled elsewhere.

## App Architecture


## Concurrency and Threading - Future and Isolates

## Final thoughts