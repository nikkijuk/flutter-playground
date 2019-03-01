# flutter-playground

Ask yourself: is it possible to create mobile hybrid apps easily? and do they look good? run fast? are cool & hip?

# current state of Flutter

Flutter has arrived 1.0 at Dec 2018

It looks like Google has made lot of right choices when developing Flutter.

- Flutter uses Dart as programming language
- Dart is statically typed, but feels familiar to javascript programmers 
- Dart compiles direclty to native and can be compiled incrementally allowing very fast development cycle  
- Ios & Android are supported out of box
- Integrations to Firebase are included

And combined with FireBase it all starts looking very bright.

- Firebase scales from simple use cases to very complex cloud environments 
- Firebase includes messaging, storage and authentication services 
- Added features for mobile incluce crashlytics

Development can be done within Andoid studio, but also other IDE's like Visual Studio Code are supported.

There are also interesting integrations also.

- Stripe has integrations to allow payment on mobile devices
- 2Dimensions has developed Flare to model vertor graphics, for which Flutter has player plugin

It's quite propable that there's more to come as platform matures.

# future Directions

Flutter should in future expand to other platforms as Android & iOs

One example is Web support, which is in experimental state (Dec 2018)

https://medium.com/flutter-io/hummingbird-building-flutter-for-the-web-e687c2a023a8

Other experimental efforts include support for developing Osx, Windows & Linux desktop applications

https://github.com/google/flutter-desktop-embedding

Flutter is also ported experimentally to Rasperry Pi, which allows Flutter apps to run without host opeting system on low capability environment

https://medium.com/flutter-io/flutter-on-raspberry-pi-mostly-from-scratch-2824c5e7dcb1

# installation

All installed components which flutter uses or needs eat up something like 3 - 4 gb disk, if not even more.

Installation takes also some time (30 – 45 min, depending on internet & memory & processor)– so: be patient

Install Flutter SDK (> 700 kb)
-	https://flutter.dev/docs/get-started/install

Install Android Studio (> 1.6 gb)
-	https://flutter.dev/docs/get-started/editor

Install android sdk + emulator + tools by opening android studio (> 2 gb)
-	https://flutter.dev/docs/get-started/install/macos#set-up-the-android-emulator

add dart and flutter plugins to android studio 
-	https://flutter.dev/docs/get-started/editor

Check installation with flutter doctor 
-	Flutter-doctor

Accept licences with flutter-doctor
-	flutter doctor --android-licenses

# first application

create new emptry project with Wizard from opening screen of Android Studio – try to open emulator – deploy your app there 

-	use scaffolding sample code
-	start emulator
-	run app

if you're lucky all works now

# learning dart

    main() => print('Hello, World!');

Dart looks familiar to developers coming from Java, JS, C/C++/C# and .. It's statically typed language and supports both functional and object oriented styles of programming. With Flutter Dart is compiled to native code just-in-time or ahead-of-time. So, fast development, but simulaneously efficently compilation for production. 

https://www.dartlang.org/

Let's see from example how classes, methods, properties and inheritance are expressed -- it should all look familiar if you have used any OO language. 

http://jpryan.me/dartbyexample/examples/inheritance/

It should be noted that there's two versions of Dart. 1.X and 2.X are close to each other, but not same. For example new is in Dart 2.X optional when creating object and mandatory in Dart 1.x.

https://www.dartlang.org/dart-2

## guides

https://www.dartlang.org/guides/language/language-tour

http://jpryan.me/dartbyexample/

## guidelines

https://www.dartlang.org/guides/language/effective-dart

## codelabs

If you are Java programmer this should help you

- Intro to Dart for Java Developers 

https://www.dartlang.org/codelabs

## interactive learning tool

https://dartpad.dartlang.org/

## tools

# learning flutter

https://flutter.io/

## books

https://www.manning.com/books/flutter-in-action

## courses

https://eu.udacity.com/course/build-native-mobile-apps-with-flutter--ud905

## codelabs

Work codelabs thru in this order. If you are experience Android developer they might feel easy. Otherwise you need some time and patience.

- Write Your First Flutter App, part 1
- Write Your First Flutter App, part 2
- Building Beautiful UIs with Flutter
- Firebase for Flutter

https://flutter.io/docs/codelabs

## articles

https://medium.com/flutter-community/building-flutter-qr-code-generator-scanner-and-sharing-app-703e73b228d3

## tools

Flutter can be plugged to hosted Continous Integration tool, which is able to produce and publish Flutter apps to Google App Store and Apple App Store with single button click. You don't even need to have Apple hardware and Xcode locally installed to produce iPhone app!

https://codemagic.io/

Free animations? Yep. And flutter has plyer for them. Sample app is available with name "the history of everything".

https://www.2dimensions.com/about-flare

https://medium.com/2dimensions/the-history-of-everything-981d989e1b45

How cool is open source? Swagger codegen for Dart is working with Flutter as one person felt implementing needed changes important enough. Think of it: If you want to generate apis for your Magento ecommerce site you just get Magentos swagger definitions, generate Dart code for your Flutter app and start calling Magentos rest api from your code. 

https://github.com/swagger-api/swagger-codegen/pull/7418

https://swagger.io/tools/swagger-codegen/

https://devdocs.magento.com/swagger/

# learning firebase

https://firebase.google.com/

## codelabs

https://codelabs.developers.google.com/?cat=Firebase

- Firebase for Flutter

# Learning angular

https://angular.io/

# Learning andoid studio

https://developer.android.com/studio/

## setup

https://flutter.io/docs/development/tools/android-studio
