## Background Tasks

1. Introduction
2. Running in the Background
  - How to run tasks in the background ?
  - 2 remaining components : **Services** and **Broadcast Receivers**
  - **Jobs** the new way android handles background task scheduling
  - Once the background task is complete a **notification** is being dispatched
3. Hydration Reminder App
  - An app which will send a notification to the user every 15 minutes (when the phone is charging) reminding him of drinking water
4. Services
  - A **Service** is an application component that can perform long-running operations in the background, and it does not provide a user interface.
  - Another application component can start a service, and it continues to run in the background even if the user switches to another application.
  - Additionally, a component can bind to a service to interact with it and even perform interprocess communication (IPC).
  - For example, a service can handle
    - network transactions,
    - play music,
    - perform file I/O, or
    - interact with a content provider, all from the background.
  - These are the three different types of services:
    - Foreground
    - Background
    - Bounded
5. Services vs. Loaders (vs. AsyncTasks vs. Threads)
  - If the task is tied to the activity lifecycle and needs to make some UI changes then use Loaders
  - If the task is independent of the current activity lifecycle and UI then use Services
  - Services, like all the core main components of Android, runs in the main thread, so if you are doing some long tasks then it will affect the main thread. In that case you have to use an AsyncTask from inside the service.
6. Quiz: Services vs. Loaders
7. Starting Services
  - There are 3 ways to start a service :
    - manually start a service (started service)
    - schedule a service (started service)
    - bind to a service (bound service)
  - When u start a service (using startService()) or schedule a service (called Jobs using JobSchedular or FirebaseJobDispatcher) the service don't interact back with the starting component. For ex: syncing database in the background.
  - While in case of a bound service, its more like a client-server interface where the service and the activity can send data to each other. For ex: playing music with updating music player UI.
8. Running Services in the Background
  - Like all the main core components of android,  services also starts on the main thread. So if required its our job to create an AsyncTask from the service and then perform the task inside the AsyncTask.
  - Service Lifecycle :
    - call to startService() by some context like an activity passing an Intent
    - onCreate()
    - onStartCommand() (run the AsyncTask here)
    - Service is Running
    - stopSelf() (called by the developer)
    - onDestroy()
    - Service is destroyed
  - Instead of managing the thread inside a service you can use an **IntentService**
9. Intent Services
  - IntentService runs in a background thread.
  - How to start an IntentService :
  ````
    //create a class and extent IntentService
    //override onHandleIntent(Intent intent) function
    //here all the background tasks are being done
    //this will also be on a separate thread

    //then in MainActivity create an intent object and pass this service just like starting another activity
    //call startService(intent)
  ````
  - Its important to note that **all IntentService requests are handled in a single background thread.** And they are issues in a sequential order.
10. Starter Code
11. Quiz: Get the Starter Code
12. Plan for Adding an IntentService
13. Exercise: Add an IntentService
14. Notifications
  - Notifications are used to notify the user about something. In our context if our background task is done we can send a notification to the user.
  - There is a long history of notifications and its recommended to check the design guidelines for them.
15. Notifications in Oreo
  - Notification Channels :
      - In the latest version of Android, Oreo, you cannot send a notification without defining the notification channel (category).
      - The user can turn on/off a particular channel of your app.
      - This gives a fine grained control to the user as to what category of notifications he wants to see in a particular app.
      - You can group channels in a Channel Group.
  - Notification Badges
  - Foreground notifications coloring
  - and much more
16. Pending Intents
    - There are 2 parts of showing a notification :
      - Creating a notification
      - When the user taps on the notification, it should open our app/activity
    - Creating the notification is the easy part, but for letting some external app to open our activity will require a Pending Intent.
    - By using Intents we can start any component explicitly or implicitly if we have the permissions to do so.
    - But what if we want to launch an activity in our application by some external application ?
    - In this case, the notifications are being displayed by a system service called NotificationsManager which is being started by the Android System. Now since we cannot change the permissions of the android system, we use Pending Intents.
    - **Pending Intents are a wrapper around our regular intent, designed to be used by other applications.**
    - It allows the other application to perform the actions mentioned in the intent as if its our application with all the permissions.
    - There are 4 methods through which you can create a pending intent :
    ````
    //PendingIntent.getActivity();
    //PendingIntent.getActivities();
    //PendingIntent.getService();
    //PendingIntent.getReceiver();
    ````
17. Exercise: Notifications
  - create a helper method to get the PendingIntent around an Explicit intent which can launch our activity.
  - get all the resources ready for display in the notification.
  - get a reference to the NotificationManager from system Services.
  - now for Android O, create a notification channel and pass it to the manager
  - create notification using the NotificationCompat.Builder class and set all the required functions.
  - set the pending intent in the setContentIntent method
  - for displaying notification call
  ````
    notificationManager.notify(id, notificationBuilder.build());
  ````
18. Notification Actions
  - after Jelly Bean (4.1 - 4.3.1) notifications can take upto 3 action buttons.
  - each action button can launch a different pending intent and perform different actions on our app.
19. Exercise: Adding Actions to Notifications
  - this adds two action buttons to the notification using addAction() function
  - for creating the action use NotificationCompat.Action class.
20. Foreground Services
  - A foreground service performs some operation that is noticeable to the user.
  - For example, an audio app would use a foreground service to play an audio track. Or google map's navigation.
  - Foreground services must display a status bar icon or a non-dismissible notification.
  - Foreground services can continue running even when the user isn't interacting with the app.
  - This increases the priority of the app.
21. Quiz: Application Priority
  - 4 general buckets :
      - Critical
        - Active applications
        - Foreground Services
      - High
        - Visible processes
      - Medium
        - Service processes
      - Low
        - Background processes
        - Empty processes
22. Issuing Reminders
  - Now lets figure out how to schedule these reminders by scheduling the service using JobSchedular.
23. Scheduling Jobs
  - Android L introduced JobScheduler to schedule jobs with constraints.
  - JobScheduler is compatible only upto API 21
  - Firebase JobDispatcher is compatible till API 9
  - *There is a note about Google Play Services which is worth checking.*
24. Exercise: Adding a JobService
25. Exercise: Schedule with FirebaseJobDispatcher
  - above 2 exercises goes deep into how to create a JobService and schedule it using FirebaseJobDispatcher
26. Broadcast Receivers
  - A broadcast receiver (receiver) is an Android component which allows you to register for system or application events.
  - All registered receivers for an event are notified by the Android runtime once this event happens.
  - Generally speaking, broadcasts can be used as a messaging system across apps and outside of the normal user flow.
  - System Broadcasts :
      - The system automatically sends broadcasts when various system events occur, such as when the system switches in and out of airplane mode.
      - The broadcast message itself is wrapped in an *Intent* object whose action string identifies the event that occurred (for example android.intent.action.AIRPLANE_MODE).
      - The intent may also include additional information bundled into its extra field. For example, the airplane mode intent includes a boolean extra that indicates whether or not Airplane Mode is on.
    - Changes to system broadcasts :
        - Android 7.0 and higher no longer sends the following system broadcasts. This optimization affects all apps, not only those targeting Android 7.0.
            - ACTION_NEW_PICTURE
            - ACTION_NEW_VIDEO
        - Apps targeting Android 7.0 (API level 24) and higher must register the following broadcasts with registerReceiver(BroadcastReceiver, IntentFilter). Declaring a receiver in the manifest does not work.
          - CONNECTIVITY_ACTION
        - Beginning with Android 8.0 (API level 26), the system imposes additional restrictions on manifest-declared receivers. If your app targets API level 26 or higher, you cannot use the manifest to declare a receiver for most implicit broadcasts (broadcasts that do not target your app specifically).
    - Receiving broadcasts :
        - Apps can receive broadcasts in two ways:
          - through manifest-declared receivers and
          - context-registered receivers
    - Security considerations and best practices :
        - If you don't need to send broadcasts to components outside of your app, then send and receive local broadcasts with the LocalBroadcastManager which is available in the Support Library.
        - Because a receiver's onReceive(Context, Intent) method runs on the main thread, it should execute and return quickly. If you need to perform long running work, be careful about spawning threads or starting background services because the system can kill the entire process after onReceive() returns.
        - Calling goAsync() in your receiver's onReceive() method and passing the BroadcastReceiver.PendingResult to a background thread. This keeps the broadcast active after returning from onReceive(). However, even with this approach the system expects you to finish with the broadcast very quickly (under 10 seconds). It does allow you to move work to another thread to avoid glitching the main thread.
    - Consider scheduling a job with the JobScheduler instead of BroadcastReceiver if thats what fits best.
27. Exercise: Show When Charging
28. Exercise: Getting the Current Battery State
29. Syncing Sunshine
30. Exercise: Synchronizing The Weather
31. Exercise: SmarterSyncing
32. Exercise: Sunshine FirebaseJobDispatcher
33. Exercise: Sunshine Notifications
34. Conclusion
