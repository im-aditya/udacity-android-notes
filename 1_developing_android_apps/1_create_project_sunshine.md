## Create Project Sunshine

1. Introduction
2. Are you ready?
3. Introducing Project Sunshine
4. A Brief Intro to Android Studio
5. Coding, GitHub and Flow
6. Quiz: Coding, GitHub and Flow
7. Creating our First Project
8. Android Min and Target Versions
  - *min sdk version* is the minimum version of the Android Operating System required to run your application.
    - The Android system will prevent the user from installing the application if the system's API Level is lower than the value specified in this attribute.
  - *target sdk version* is the version of Android that your app was created to run on.
    - Specifying this target version allows the platform to disable compatibility settings that are not required for the target version (which may otherwise be turned on in order to maintain forward-compatibility) or enable newer features that are not available to older applications.
  - *compile sdk version* is the the version of Android SDK that the build tools uses to compile & build the application in order to release, run, or debug.
  - Usually the compile sdk version and the target sdk version are the same.
9. Setting Min and Target
  - can use the app's build.gradle file
  - go to project structure -> app -> flavour tab
10. Running Your Code
11. Android Software Stack
   - Execution Process :
       - We start with the Android project
       - Gradle, which is a build & dependency management system, builds the project and package the byte code with all the resources and manifest files into an APK file
       - Then it is being signed and pushed to the device using the ADB.
   - Consists of 5 layers :
       1. Linux Kernel
         - Consists of all the drivers for interacting with the hardware
       2. Hardware Abstraction Layer (HAL)
         - provides standard interfaces that expose device hardware capabilities to the higher-level Java API framework
       3. Android Runtime
         - For devices running Android version 5.0 (API level 21) or higher, each app runs in its own process and with its own instance of the Android Runtime (ART).
         - ART is written to run multiple virtual machines on low-memory devices by executing **DEX** files, a bytecode format designed specially for Android that's optimized for minimal memory footprint.
         - Build toolchains, such as *Jack*, compile Java sources into DEX bytecode, which can run on the Android platform.
         - Some of the major features of ART include the following:
           - Ahead-of-time (AOT) and just-in-time (JIT) compilation
           - Optimized garbage collection (GC)
           - Better debugging support, including a dedicated sampling profiler, detailed diagnostic exceptions and crash reporting, and the ability to set watchpoints to monitor specific fields
         - Prior to Android version 5.0 (API level 21), **Dalvik was the Android runtime**. If your app runs well on ART, then it should work on Dalvik as well, but the reverse may not be true.
       4. Native C/C++ Libraries
         - Many core Android system components and services, such as ART and HAL, are built from native code that require native libraries written in C and C++.
         - The Android platform provides Java framework APIs to expose the functionality of some of these native libraries to apps.
         - For example, you can access OpenGL ES through the Android framework’s Java OpenGL API to add support for drawing and manipulating 2D and 3D graphics in your app.
       5. Java API Framework
         - The entire feature-set of the Android OS is available to you through APIs written in the Java language.
       6. System Apps
12. Activities, Packages, and Layouts
13. Quiz: Android Basics
14. Android Layouts Primer
15. Exercise: Framing Favorite Toys
16. Exercise: Toying with FavoriteToys
17. Exercise: See More FavoriteToys
18. Visual Layout Editor
19. Handling Different Screen
20. Responsive Design
21. Layout Managers
22. Exercise: Update Sunshine Layout
23. Solution: Update Sunshine Layout
24. Exercise: Add Scrolling Weather
25. Solution: Add Scrolling Weather
26. Recap
