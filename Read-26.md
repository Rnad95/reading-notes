# Application Fundamentals

## Definition

**Android** is a mobile operating system based on a modified version of the Linux kernel and other open source software, designed primarily for touchscreen mobile devices such as smartphones and tablets.

The Architecture of Android studio contains: System App which is the user can see, Java API Framework that the developer can access to link the System app and the native c/C++ Libraries. Also, It has Android Runtime (ART) to run the application. then, the Hard Abstraction Layer (HAL). Finally we have a Linux Kernel.

- The Architecture of Android has shown below:

![Arch of Android](https://i.ibb.co/Cvrmjq4/Screenshot-from-2022-04-24-08-13-17.png)

This is the basic Android, then the developer improve this architecture

## Resources

---
Android apps can be written using Kotlin, Java, and C++ languages. The Android SDK tools compile your code along with any data and resource files into an APK or an Android App Bundle.

- An Android package, which is an archive file with an .apk suffix, contains the contents of an Android app that are required at runtime and it is the file that Android-powered devices use to install the app.

- An Android App Bundle, which is an archive file with an .aab suffix, contains the contents of an Android app project including some additional metadata that is not required at runtime

Each Android app lives in its own security sandbox, protected by the following Android security features:

- The Android operating system is a multi-user Linux system in which each app is a different user.

- By default, the system assigns each app a unique Linux user ID (the ID is used only by the system and is unknown to the app). The system sets permissions for all the files in an app so that only the user ID assigned to that app can access them.

- Each process has its own virtual machine (VM), so an app's code runs in isolation from other apps.
- By default, every app runs in its own Linux process. The Android system starts the process when any of the app's components need to be executed, and then shuts down the process when it's no longer needed or when the system must recover memory for other apps.

## App components

App components are the essential building blocks of an Android app. Each component is an entry point through which the system or a user can enter your app. Some components depend on others.

### There are four different types of app components:

### 1. Activities:  

An activity is a single, focused thing that the user can do. Almost all activities interact with the user, so the Activity class takes care of creating a window for you in which you can place your UI with setContentView(View).

There are three key loops you may be interested in monitoring within your activity: entire lifetime, visible lifetime, and foreground lifetime.

The life cycle of Activity is shown below:

![Life cycle of Activity](https://developer.android.com/images/activity_lifecycle.png)

### 2. Services

A service is a general-purpose entry point for keeping an app running in the background for all kinds of reasons. It is a component that runs in the background to perform long-running operations or to perform work for remote processes

There are two types of services that tell the system how to manage an app: started services and bound services: started services, Bound services, and Broadcast receivers.

### 3. Broadcast receivers

A broadcast receiver is a component that enables the system to deliver events to the app outside of a regular user flow, allowing the app to respond to system-wide broadcast announcements. Because broadcast receivers are another well-defined entry into the app, the system can deliver broadcasts even to apps that aren't currently running

### 4. Content providers

A content provider manages a shared set of app data that you can store in the file system, in a SQLite database, on the web, or on any other persistent storage location that your app can access. Through the content provider, other apps can query or modify the data if the content provider allows it.

There are a few particular things this allows the system to do in managing an app:

- Assigning a URI doesn't require that the app remain running, so URIs can persist after their owning apps have exited. The system only needs to make sure that an owning app is still running when it has to retrieve the app's data from the corresponding URI.
- These URIs also provide an important fine-grained security model. For example, an app can place the URI for an image it has on the clipboard, but leave its content provider locked up so that other apps cannot freely access it. When a second app attempts to access that URI on the clipboard, the system can allow that app to access the data via a temporary URI permission grant so that it is allowed to access the data only behind that URI, but nothing else in the second app.

## Activating components

Three of the four component types—activities, services, and broadcast receivers—are activated by an asynchronous message called an intent. Intents bind individual components to each other at runtime. You can think of them as the messengers that request an action from other components, whether the component belongs to your app or another.

There are separate methods for activating each type of component:

- You can start an activity or give it something new to do by passing an Intent to startActivity() or startActivityForResult() (when you want the activity to return a result).

- With Android 5.0 (API level 21) and later, you can use the JobScheduler class to schedule actions. For earlier Android versions, you can start a service (or give new instructions to an ongoing service) by passing an Intent to startService(). You can bind to the service by passing an Intent to bindService().

- You can initiate a broadcast by passing an Intent to methods such as sendBroadcast(), sendOrderedBroadcast(), or sendStickyBroadcast().

- You can perform a query to a content provider by calling query() on a ContentResolver.

## The manifest file

Before the Android system can start an app component, the system must know that the component exists by reading the app's manifest file, AndroidManifest.xml. Your app must declare all its components in this file, which must be at the root of the app project directory.

The manifest does a number of things in addition to declaring the app's components, such as the following:

Identifies any user permissions the app requires, such as Internet access or read-access to the user's contacts.
Declares the minimum API Level required by the app, based on which APIs the app uses.
Declares hardware and software features used or required by the app, such as a camera, bluetooth services, or a multi-touch screen.
Declares API libraries the app needs to be linked against (other than the Android framework APIs), such as the Google Maps library.

## App resources

- An Android app is composed of more than just code. It requires resources that are separate from the source code, such as images and audio files. Using app resources makes it easy to update various characteristics of your app without modifying code. Providing alternative resources enables you to optimize your app for a variety of device configurations. Android supports many different qualifiers for your alternative resources.

- A qualifier is a short string that you include in the name of your resource directories. These strings are used to define the device configuration for which those resources should be used. For example, you can create different layouts for your activities, depending on the device's screen orientation and size.

## Resources

---

1. [Wikipedia](https://en.wikipedia.org/wiki/Android_(operating_system))

2. [Android Documentation](https://developer.android.com/guide/components/fundamentals)