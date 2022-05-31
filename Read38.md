# Read: 38 - Notifications

## Intents and Intent Filters

---

An Intent is a messaging object you can use to request an action from another app component. Although intents facilitate communication between components in several ways, there are three fundamental use cases: Starting an activity
, Starting a service, and Delivering a broadcast

**Intent types:**

There are two types of intents: Explicit and implicit

Figure shown below how an intent is used when starting an activity. When the Intent object names a specific activity component explicitly, the system immediately starts that component.

![intent ype](https://developer.android.com/images/components/intent-filters_2x.png)

An intent filter is an expression in an app's manifest file that specifies the type of intents that the component would like to receive.

For instance, by declaring an intent filter for an activity, you make it possible for other apps to directly start your activity with a certain kind of intent. Likewise, if you do not declare any intent filters for an activity, then it can be started only with an explicit intent.

**Building an intent:**

An Intent object carries information that the Android system uses to determine which component to start (such as the exact component name or component category that should receive the intent), plus information that the recipient component uses in order to properly perform the action (such as the action to take and the data to act upon).

Without a component name, the intent is implicit and the system decides which component should receive the intent based on the other intent information (such as the action, data, and category—described below).

In the case of a broadcast intent, this is the action that took place and is being reported.
See the Intent class reference for more constants that define generic actions.

Always use setDataAndType() to set both URI and MIME type.
If you need to declare your own extra keys (for intents that your app receives), be sure to include your app's package name as a prefix, as shown in the following example:

    Java static final String EXTRA_GIGAWATTS = "com.example.

**Example explicit intent:**

    // Executed in an Activity, so 'this' is the Context
    // The fileUrl is a string URL, such as "http://www.example.com/image.png"
    Intent downloadIntent = new Intent(this, DownloadService.class);
    downloadIntent.setData(Uri.parse(fileUrl));
    startService(downloadIntent);

**Example implicit intent:**

    // Create the text message with a string.
    Intent sendIntent = new Intent();
    sendIntent.setAction(Intent.ACTION_SEND);
    sendIntent.putExtra(Intent.EXTRA_TEXT, textMessage);
    sendIntent.setType("text/plain");

    // Try to invoke the intent.
    try {
    startActivity(sendIntent);
    } catch (ActivityNotFoundException e) {
    // Define what your app should do if no activity can handle the intent.
    }

**Forcing an app chooser:**

When there is more than one app that responds to your implicit intent, the user can select which app to use and make that app the default choice for the action.

The chooser dialog asks the user to select which app to use for the action (the user cannot select a default app for the action).
For example, when your app performs "share" with the ACTION_SEND action, users may want to share using a different app depending on their current situation, so you should always use the chooser dialog, as shown in Figure below.

![](https://developer.android.com/images/training/basics/intent-chooser.png)

To show the chooser, create an Intent using createChooser() and pass it to startActivity(), as shown in the following example.

This example displays a dialog with a list of apps that respond to the intent passed to the createChooser() method and uses the supplied text as the dialog title.

    Intent sendIntent = new Intent(Intent.ACTION_SEND);
    ...

    // Always use string resources for UI text.
    // This says something like "Share this photo with"
    String title = getResources().getString(R.string.chooser_title);
    // Create intent to show the chooser dialog
    Intent chooser = Intent.createChooser(sendIntent, title);

    // Verify the original intent will resolve to at least one activity
        if (sendIntent.resolveActivity(getPackageManager()) != null) {
        startActivity(chooser);
    }

**Check for unsafe intent launches:**

To check for unsafe intent launches in your app, call detectUnsafeIntentLaunch() when you configure your VmPolicy, as shown in the following code snippet. If your app detects a StrictMode violation, you might want to stop app execution to protect potentially sensitive information.

    protected void onCreate() {
        StrictMode.setVmPolicy(new VmPolicy.Builder()
            // Other StrictMode checks that you've previously added.
            // ...
            .detectUnsafeIntentLaunch()
            .penaltyLog()
            // Consider also adding penaltyDeath()
            .build());
    }

**Use intents more responsibly:**

Use a PendingIntent instead of a nested intent. That way, when another app unparcels the PendingIntent of its containing Intent, the other app can launch the PendingIntent using the identity of your app. This configuration allows the other app to safely launch any component, including a non-exported component, in your app.

The diagram in figure 2 shows how the system passes control from your (client) app to another (service) app, and back to your app:

Your app creates an intent that invokes an activity in another app. Within that intent, you add a PendingIntent object as an extra. This pending intent invokes a component in your app; this component isn't exported.
Upon receiving your app's intent, the other app extracts the nested PendingIntent object.

The other app invokes the send() method on the PendingIntent object.
After passing control back to your app, the system invokes the pending intent using your app's context.

inter-app communication when using a nested pending intent shown in image below:

![](https://developer.android.com/images/guide/components/nested-pending-intent.svg)

## Allowing Other Apps to Start Your Activity 

---
If your app can perform an action that might be useful from another app, your app should be prepared to respond to action requests by specifying the appropriate intent filter in your activity.

**Add an Intent Filter:**

The system may send a given Intent to an activity if that activity has an intent filter fulfills the following criteria of the Intent object: Action, data, and Category

    <activity android:name="ShareActivity">
    <intent-filter>
        <action android:name="android.intent.action.SEND"/>
        <category android:name="android.intent.category.DEFAULT"/>
        <data android:mimeType="text/plain"/>
        <data android:mimeType="image/*"/>
    </intent-filter>
</activity>

**Handle the Intent in Your Activity:**

call getIntent() to retrieve the Intent that started the activity. You can do so at any time during the lifecycle of the activity, but you should generally do so during early callbacks such as onCreate() or onStart().

    @Override
    protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);

    setContentView(R.layout.main);

    // Get the intent that started this activity
    Intent intent = getIntent();
    Uri data = intent.getData();

    // Figure out what to do based on the intent type
    if (intent.getType().indexOf("image/") != -1) {
        // Handle intents with image data ...
    } else if (intent.getType().equals("text/plain")) {
        // Handle intents with text ...
    }
    }

**Return a Result:**

If you want to return a result to the activity that invoked yours, simply call setResult() to specify the result code and result Intent. When your operation is done and the user should return to the original activity, call finish() to close (and destroy) your activity

## Intent matching

---

Intents are matched against intent filters not only to discover a target component to activate, but also to discover something about the set of components on the device.
Your application can use intent matching in a manner similar to what the Home app does.

For example, queryIntentActivities() returns a list of all activities that can perform the intent passed as an argument, and queryIntentServices() returns a similar list of services.
Neither method activates the components; they just list the ones that can respond.
There's a similar method, queryBroadcastReceivers(), for broadcast receivers.
