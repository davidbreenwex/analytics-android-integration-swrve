analytics-android-integration-swrve
======================================

Swrve integration for [analytics-android](https://github.com/segmentio/analytics-android).

## Installation

In your top-level project `build.gradle` add:

```
repositories {
    jcenter{
        url = 'http://dl.bintray.com/swrve-inc/android'
    }
    maven {
        url = 'https://maven.google.com'
    }
}
```

To install the Segment-Swrve integration, simply add this line to your gradle file:

```
dependencies {
    compile 'com.segment.analytics.android:analytics:4.0.4'
    compile 'com.swrve.segment:analytics-android-integration-swrve:1.1.1'
}
```

## Usage

After adding the dependency, you must register the integration with our SDK.  To do this, import the Swrve integration:


```
import com.swrve.segment.SwrveIntegration;
```

And add the following line:

```
int appId = -1;
String apiKey = "api_key";

SwrveConfig swrveConfig = new SwrveConfig();
// To use the EU stack, include this in your config.
// swrveConfig.setSelectedStack(SwrveStack.EU);

Analytics analytics = new Analytics.Builder(this, "write_key")
                          .use(SwrveIntegration.createFactory(application, appId, apiKey, swrveConfig)
                          .build();
```

## Install Specific Version of Swrve SDK

By default this integration pulls in the latest vanilla version of the Swrve SDK. If you rather want to use a specific version, simply exclude them from the integration and specify the required versions in your `build.gradle` file directly.

For example, if you wanted to use the Firebase flavored Swrve SDK:

```
compile('com.swrve.segment:analytics-android-integration-swrve:1.1.1') {
    exclude group: 'com.swrve.sdk.android', module: 'swrve'
}
compile 'com.swrve.sdk.android:swrve-firebase:5.3.0'
```

License
-------
© Copyright Swrve Mobile Inc or its licensors. Distributed under the [Apache 2.0 License](LICENSE).  
Google Play Services Library Copyright © 2012 The Android Open Source Project. Licensed under the [Apache 2.0 License](http://www.apache.org/licenses/LICENSE-2.0).  
Gradle Copyright © 2007-2011 the original author or authors. Licensed under the [Apache 2.0 License](http://www.apache.org/licenses/LICENSE-2.0).
