---
layout: post
title: "Android Studio - Github PagerSlidingTabStrip Project Build Error"
date: 2014-07-11 18:57:58 +0800
comments: true
categories: [Android, Android Studio, Gradle]
keywords: Android, Studio, Gradle, Build, Error, PagerSlidingTabStrip
description: Android Studio - Github PagerSlidingTabStrip Project Build Error
---

I imported Github PagerSlidingTabStrip project into Android Studio 0.8.2.

Oops. And it wasted me a lot of time to fix build error.

To avoid encountered the same problems.

I noted solutions here and hoped this can help you. :)

<!--more -->

###Build Error 1.###
```
Error:Build script error, unsupported Gradle DSL method found: 'getBootClasspath()'!

Possible causes could be:
  - you are using Gradle version where the method is absent Fix Gradle settings
  - you didn't apply Gradle plugin which provides the method Apply Gradle plugin
  - or there is a mistake in a build script Goto source
```
Modified PagerSlidingTabStrip / build.gradle.
```
---classpath 'com.android.tools.build:gradle:0.6.+'
+++classpath 'com.android.tools.build:gradle:0.12.+'

```

Modified PagerSlidingTabStrip / gradle / wrapper / gradle-wrapper.properties
```
---distributionUrl=http\://services.gradle.org/distributions/gradle-1.8-all.zip
+++distributionUrl=http\://services.gradle.org/distributions/gradle-1.12-all.zip
```

###Build Error 2.###
```
Error:Could not find property 'allJava' on source set main.
```

Modified PagerSlidingTabStrip / library / build.gradle
```
---apply from: 'https://raw.github.com/chrisbanes/gradle-mvn-push/master/gradle-mvn-push.gradle'
```

Reference : [Github PagerSlidingTabStrip Project](https://github.com/astuetz/PagerSlidingTabStrip)
