# Read: 27 - Intents, Activities, and SharedPreferences

## 1. **Save key-value data**

 SharedPreferences object points to a file containing key-value pairs and provides simple methods to read and write them. Each SharedPreferences file is managed by the framework and can be private or shared.

 ![definition](https://tutorial.eyehunts.com//wp-content/uploads/2018/07/Android-SharedPreferences-Tutorial-Save-Key-Value-data-example-in-kotlin-1.png)

### Get a handle to shared preferences

---
You can create a new shared preference file or access an existing one by calling one of these methods:

getSharedPreferences() — Use this if you need multiple shared preference files identified by name, which you specify with the first parameter. You can call this from any Context in your app.
getPreferences() — Use this from an Activity if you need to use only one shared preference file for the activity. Because this retrieves a default shared preference file that belongs to the activity, you don't need to supply a name.

**EXAMPLE**

![Java example](https://i.ibb.co/dLs5Q7X/Screenshot-from-2022-04-26-14-26-56.png)

But alternatively, if you need just one shared preference file for your activity, you can use the getPreferences() method:

![Alternative](https://i.ibb.co/TRtMV8Q/Screenshot-from-2022-04-26-14-28-01.png)

### Write to shared preferences

---
To write to a shared preferences file, create a `SharedPreferences.Editor` by calling `edit()` on your `SharedPreferences`. Then we can do `apply()` or `commit()`

### Read from shared preferences

---
If we need to retrieve the data we use:
![retrieve the data](https://i.ibb.co/Qnqg1WN/Screenshot-from-2022-04-26-14-30-10.png)

## 2. **Tasks and the back stack**

is a definition which talking about push the current activity and put above it a new activity in the back stack which allows to the back button to reverse this.

### Lifecycle of a task and its back stack

---
Home screen is the starting place for most tasks. When a user touches the icon for an app or shortcut in the app launcher, that app's task comes to the foreground. If no task exists for the app (the app has not been used recently). Then a new task is created and the main activity for that app opens as the root activity in the stack.

When an activity stops, the system retains the current state of its user interface. When the user performs the back action, the current activity is popped from the top of the stack (the activity is destroyed) and the previous activity resumes. Figure 1 visualizes this behavior with a timeline showing the progress between activities along with the current back stack at each point in time.

![add an item](https://developer.android.com/images/fundamentals/diagram_backstack.png)

### Back press behavior for root launcher activities

When a user presses or gestures Back from a root launcher activity, the system handles the event differently depending on the version of Android that the device is running. Root launcher activities are activities that declare an Intent filter with both `ACTION_MAIN` and `CATEGORY_LAUNCHER`. These activities act as entry points into your app from the app launcher and are used to start a task.

In Android 11 and lower the The system finishes the activity meanwhile in Android 12 and higher the system moves the activity and its task to the background instead of finishing the activity. This behavior matches the default system behavior when navigating out of an app using the Home button or gesture.

Calling `super.onBackPressed()` moves the activity and its task to the background when appropriate and provides a more consistent navigation experience for users across apps. In most cases, this means that users can more quickly resume your app from a warm state, instead of having to completely restart the app. If you need to provide custom back navigation, we recommend using the AndroidX Activity APIs.

### Background and foreground tasks

---

A task is a cohesive unit that can move to the background when a user begins a new task or goes to the Home screen. While in the background, all the activities in the task are stopped, but the back stack for the task remains intact. A task can then return to the foreground so users can pick up where they left off.

How do you create a task flow for an app that has multiple activities, each with its own stack of activities? The user uses the Home button or gesture to start a new app from the app launcher. When the new app starts, the system starts a task for that app (Task A) and puts Task A into the background. The user can switch back to Task A by going Home and selecting the app icon that started that task.

### Multiple activity instances

---
If your app allows users to start a particular activity from more than one task, a new instance of that activity is created and pushed onto the stack. One activity in your app might be instantiated multiple times (even from different tasks). If the user navigates backward using the Back button or gesture, each instance of the activity is revealed in the order they were opened (each with their own UI state).

### Lifecycle recap

---

When the user leaves a task using the Home button or gesture, the current activity is stopped and its task goes into the background. If the user later resumes the task by selecting the launcher icon that began the task, the task comes to the foreground and resumes the previous activity. When an activity is destroyed, the system does not retain the activity's state.

### Manage tasks

---

The way Android manages tasks and the back stack, as described above, works great for most apps. However, you might decide that you want to interrupt the normal behavior.

Perhaps you want an activity to begin a new task when it is started instead of being placed within the current task. Or, you want your back stack to be cleared of all activities except for the root activity when the user leaves the task.

You can do these things and more, with attributes in the `<activity>` manifest element and with flags in the intent that you pass to `startActivity()`.

In this regard, these are the principal `<activity>` attributes that you can use:

- `taskAffinity`  
- `launchMode`  
- `allowTaskReparenting`  
- `clearTaskOnLaunch`  
- `alwaysRetainTaskState`  
- `finishOnTaskLaunch`  

And these are the principal intent flags that you can use:

- `FLAG_ACTIVITY_NEW_TASK`
- `FLAG_ACTIVITY_CLEAR_TOP`
- `FLAG_ACTIVITY_SINGLE_TOP`

### Defining launch modes

---

You can define different launch modes for an activity when it starts. Launch modes in two way:

1. Using the manifest file
2. Using Intent flags

Activity A can define in its manifest how it should associate with the current task and Activity B can also request how to associate with current task. If both Activities A and B define how Activity B should associated with a task, then Activity A's request is honored over Activity B's request.

### Define launch modes using the manifest file

---
When declaring an activity in your manifest file, you can specify how the activity should associate with a task using the  element's launchMode attribute. There are four different launch modes you can assign to the launch mode attribute.

 There are four different launch modes you can assign to the launchMode attribute:

- standard (`Default`): An activity can be instantiated multiple times, each instance can belong to different tasks, and one task can have multiple instances. The system creates a new instance of the activity in the task from which it was started and routes the intent to that instance directly within the task.

- singleTop: Activity can be instantiated multiple times. Each instance can belong to different tasks, and one task can have multiple instances. If an intent arrives for an activity of type B, then a new instance of B is added to the stack, even if its launch mode is "singleTop".

- singleTask: An activity is an object that sits at the root of a task and all other activities on top of it are destroyed. The system routes the intent to existing instance through its `onNewIntent()` method, rather than creating a new instance for each new task.

- singleInstance: Any activities started by this one open in a separate task for each member of the "singleTask" instance.

- singleInstancePerTask: An activity can only be running as the root activity of the task, and therefore there will only be one instance of this activity in a task. In contrast to the singleTask launch mode, this activity can be started in multiple instances in different tasks if the `FLAG_ACTIVITY_MULTIPLE_TASK` or `or FLAG_ACTIVITY_NEW_DOCUMENT`
 is set.

 ![explain the stack](https://i.ytimg.com/vi/m8sf0UkJkxo/mqdefault.jpg)

The Back button and gesture always take the user to the previous activity. If you start an activity that specifies the singleTask launch mode, then if an instance exists in a background task, that whole task is brought to the foreground. At this point, the back stack now includes all activities from that task brought forward, at the top of the stack. The figure below illustrate that:

![image](https://developer.android.com/images/fundamentals/diagram_backstack_singletask_multiactivity.png)

### Define launch modes using Intent flags

---

When starting an activity, you can modify the default association of an activity to its task by including flags in the intent that you deliver to startActivity(). The flags you can use to modify the default behavior are:

- `FLAG_ACTIVITY_NEW_TASK` : If a task is already running for the activity you are now starting, that task is brought to the foreground with its last state restored and the activity receives the new intent in onNewIntent().

- `FLAG_ACTIVITY_SINGLE_TOP` : If the activity being started is the current activity, then the existing instance receives a call to `onNewIntent()` instead of creating a new instance. This produces the same behavior as the "singleTop" launchMode value, discussed in the previous section.

- `FLAG_ACTIVITY_CLEAR_TOP` : There is no value for the launchMode attribute that produces this behavior. If the activity being started is already running in the current task, then instead of launching a new instance of that activity, all of the other activities on top of it are destroyed and this intent is delivered to the resumed instance. When used together, these flags are a way of locating an existing activity in another task and putting it in a position where it can respond to the intent.

### Handle affinities

---

- An affinity indicates which task an activity prefers to belong to. By default, all activities in the same app have an affinity for each other.  
- You can modify the default affinity for an activity. Activities defined in different apps can share an affinity, or activities defined in the  same app can be assigned different task affinities.  
- You can modify the affinity for any given activity with the taskAffinity attribute of the  element.

- The affinity comes into play in two circumstances:

1. When the intent that launches an activity contains the `FLAG_ACTIVITY_NEW_TASK` flag.

2. When an activity has its `allowTaskReparenting` attribute set to "true".

### Clear the back stack

---

If the user leaves a task for a long time, the system clears the task of all activities except the root activity. The system behaves this way, because after an extended amount of time, users likely have abandoned what they were doing before and are returning to the task.

### Start a task

---
You can set up an activity as the entry point for a task by giving it an intent filter with "android.intent.action.MAIN" as the specified action and "android.intent.category.LAUNCHER" as the specified category

![action](https://i.ibb.co/rfZphKd/Screenshot-from-2022-04-26-14-19-29.png)