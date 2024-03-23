---
title: "Developing for Flutter as an Android Developer"
date: 2024-03-23 17:09:00 +0100
categories: [Flutter]
tags: [flutter, development, programming]
---

Somehow I had a bad feeling before developing mobile apps with **Flutter**.
As a software developer I came across different languages and felt just at home with Kotlin for Android.
Flutter uses yet another programming language and in the past non-native cross-platform frameworks had a bad reputation.

This article should give an overview on Flutter with Dart, how it is similar to Android and some thoughts on using it.

## Dart - Another programming language
There are many well established programming languages. So why did the Flutter Team to decide to use another one?
In the official _[Flutter FAQ](https://docs.flutter.dev/resources/faq#why-did-flutter-choose-to-use-dart)_ it is stated 
that several reasons like "Fast allocations", "Predictable, high performance" and "Object-orientation" helped to decide
for Dart as the main language, but the main reasons were probably the *JIT* (Just-In-Time compiler) with the possibility
to instantly reload the current view or the app on device after code change, and the Ahead-Of-Time compiler.

The first thing I instantly liked was the JIT features like *Hot Reload* for loading code changes and reloading 
the current state and *Hot Restart*, which is the same as Hot Reload but restarts the app and therefore the app's state is lost.

The deployment to the *Dart VM* which is used to run the Flutter code takes significantly less time than recompiling code for your platform.
You can also find other cases where the *Hot Reload* / *Hot Restart* won't succeed under 
_[Hot Reload](https://docs.flutter.dev/tools/hot-reload)_.
Previewing your Widgets on different screen sizes and layouts in your Inspector is still a missing feature for Flutter as of my knowledge. 
There is the package device_preview so you can compare the layout on many different devices but only when deployed. 
In newer Android Studio Versions you can preview your Compose Views more easily on different screen sizes at once
 _([Compose Previews](https://developer.android.com/jetpack/compose/tooling/previews))_. 
 Since Android Studio Giraffe you can also use _[LiveEdit](https://developer.android.com/jetpack/compose/tooling/iterative-development#live-edit)_
 to recompile your UI but only for Compose 1.3 or newer (more limitations apply). There Flutter has an advantage with Hot reload which 
 was there at the beginning and and is not limited to the UI.

As a Kotlin Developer it didn't take much time to understand the language features and syntax of *Dart*. Some parts like 
double colons at the end of the line and function declarations felt like C/C++. Other parts like dynamic types and extensions
are not so much different to Kotlin. 
Even when you get lost, the documentation and guides of the Flutter team are very helpful. There is basically a guide for
every type of programmer who is new to Flutter, so there is also a 
[Guide for Android Developer](https://docs.flutter.dev/get-started/flutter-for/android-devs)_ and other backgrounds, so you can 
translate your knowledge from other languages much faster.

## App Architecture
There are many design patterns for software architecture in mobile app development. All serve different philosophies and
styles. This part will not cover details on how to accomplish the patterns in Flutter but should give an overview on
features of Dart and Flutter that fulfill needs in design.

### UI - Everything is a Widget (until it's not)
If you are familiar to declarative frameworks like *Swift UI* or *Jetpack Compose* than you should have a quick start
with the *Widget* Structure of Flutter code. 

Most UI elements of a Flutter app are nested Widgets. A so called *Widget Tree* defines the Layout, painting of the canvas and
how user interactions are handled. In the _[Widget Catalog](https://docs.flutter.dev/ui/widgets)_ you can find a widget for your use-case.

There are two kinds of _[Widgets](https://api.flutter.dev/flutter/widgets/Widget-class.html)_ in Flutter:
When a Widget won't change or should not control the state itself, you can use a *StatelessWidget*.
When you want Flutter to manage state changes of your UI you can use a *StatefulWidget*.
Setting a state within a *StatefulWidget* is as easy as to call *setState* in a UI method.

You not only declare UI in your Widget but also provide dependencies like repositories or models for example with the famous *BLoC* 
package. Settings or navigation routes can also be provided within Widgets. Most of the time you can consume these configurations 
via the context parameter in the current Widget. All of this seems similar to *Jetpack Compose* on Android, but when it comes to the layout,
there are some differences: You would use modifiers in Compose to control position and size, when for most cases in Flutter you would
use another Widget as parent of your component you want to modify.

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
          padding: const EdgeInsets.all(8.0),
          child: Text('Hello Flutter')
        ),
      ),
    );
  }
}
```

As described in
_[Architectural Overview - Widgets](https://docs.flutter.dev/resources/architectural-overview#widgets)_ the code for UI
should not contain side effects since it could potentially be called each frame. That also apply for composable code 
where you should take care of code that is not part of the composition (See _[Side Effects](https://developer.android.com/jetpack/compose/side-effects)_).

So *Widgets* are basically classes that contain code for composing the UI (with passing references) and should be designed for 
fast execution. Different logic should be handled elsewhere.

### Object Orientation (OOP)
Dart is an object oriented, type safe, sound null safe language, that also provide a dynamic type when flexibility is needed
_([Dart: Overview - Language](https://dart.dev/overview#language))_.
Dart also supports Generics.
Some features and extensions like Reflections need to be added from [pub.dev](https://pub.dev) the official package repository managed by Google.

### Dependency Injection
The Flutter framework is by design very thin and has limited support for dependency injection by default.
There are certain frameworks like _provider_ and _bloc_ that use the Widget tree structure as entry point to provide 
dependencies that can be consumed via reference in the build context of a child Widget _([BuildContext](https://api.flutter.dev/flutter/widgets/BuildContext-class.html))_.
Here is a simple app example with ChangeNotifierProvider of the _provider_ package for Dependency Injection:

```Dart
void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({super.key});
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Dependency Injection with provider',
      home: ChangeNotifierProvider<TestRepository>(
        create: (context) => TestRepositoryImpl(),
        child: const MyHomePage(),
      ), // provide implementation
    );
  }
}

class MyHomePage extends StatelessWidget {
  const MyHomePage({super.key});

  @override
  Widget build(BuildContext context) {
    final repository = Provider.of<TestRepository>(context);
    return Center(
      child: Text(repository.text),
    );
  }
}

abstract class TestRepository extends ChangeNotifier {
  String get text;
}

class TestRepositoryImpl extends TestRepository {
  @override
  String get text => 'Hello Dependency';
}
```

### Asynchronous Programming 
The Flutter team recommends to use the main isolate (basically a representation of the main thread) for most code.
If the execution needs more time e.g. when accessing an API, it is recommended to call code asynchronous.

A function needs to return a _Future_ of type T
to make it callable in an asynchronous way. When you need to wait for the result, you can use the _await_ keyword.
This can only happen when the code lives in a scope that is prepended with the _async_ keyword and returns a _Future_.
This is similar to using _async_ builder as one way of creating Kotlin _Coroutines_ described in _[Concurrency](https://kotlinlang.org/docs/coroutines-and-channels.html#concurrency)_.

The _Future_ class serves as a promise on an return type T when the execution was successful.

```Dart
Future<String> getText() async {
  var text = await fetchText();
  return text;
}

Future<String> fetchText() =>
    Future.delayed(
      const Duration(seconds: 3),
      () => 'Hello World',
    );

Future<void> main() async {
  print(await createOrderMessage());
} // even the main function can be executed asynchronously
```

### Concurrency and Multithreading
When there are CPU or IO heavy tasks that can't run in smaller junks with async/await on the main isolate 
(the default isolate your code lives in) and therefor would overshoot the frame gap the UI stutters.
In Dart you can create a new separate _[Isolate](https://docs.flutter.dev/perf/isolates)_ independent from your starting code. 
When you want to have communication between Isolates you can define ports and listen on them.
Accessing memory of Isolates is limited. You can only send messages between Isolates and memory can only be changed in
the owning Isolate.

## Final Thoughts
Even though you have to learn a new language, the Flutter documentation and guides make it really easy to get started.
As an Android Developer you have a solid foundation which gives an easy entry and you can rely on solid packages. 
You also have access to native code via protobuf defined interfaces (A topic that I didn't cover here https://protobuf.dev/getting-started/darttutorial/) 
so you can use your Kotlin packages to access specific sensors. 
So overall I highly recommend to checkout Flutter when you plan on deploying an app for more than one platform or you
have a short (time) budget, since _Hot Reload/Refresh_ provides the basis for fast iterations.