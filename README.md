# ![AppSpector](https://github.com/appspector/ios-sdk/raw/master/appspector-logo.png)

With AppSpector you can remotely debug your app running in the same room or on another continent. 
You can measure app performance, view database content, logs, network requests and many more in realtime. 
This is the instrument that you've been looking for. Don't limit yourself only to simple logs. 
Debugging don't have to be painful!

## Getting Started
Each app you want to use with AppSpector SDK you have to register on the web (https://app.appspector.com).
After adding the application navigate to app settings and copy API key.

<!-- integration-manual-start -->
You can integrate AppSpector SDK linking to the framework manually or using Cocoapods.
To manually link just download AppSpectorSDK.zip, extract it and drop AppSpectorSDK.framework to your XCode project.
Then navigate to your project settings and under 'General' tab add AppSpectorSDK framework to 'Embedded Binaries' section.
<!-- integration-manual-end -->

<!-- integration-pods-start -->
To use cocoapods add this line to your podfile and run `pod install`:

```
pod 'AppSpectorSDK', :podspec => 'https://raw.githubusercontent.com/appspector/ios-sdk/master/AppSpectorSDK.podspec'
```
<!-- integration-pods-end -->

[Join our slack to discuss setup process and features](https://slack.appspector.com)

## Features
AppSpector provides 7 monitors that tracks different activities inside your app:

#### Screenshot monitor
Simply captures screenshot from the device.

#### SQLite monitor
Provides browser for sqlite databases found in your app. Allows to track all queries, shows DB scheme and data in DB. You can issue custom SQL query on any DB and see results in browser immediately.

#### HTTP monitor
Shows all HTTP traffic in your app. You can examine any request, see request/response headers and body.
We provide XML and JSON highliting for request/responses with formatting and folding options so even huge responses are easy to look through.

#### CoreData monitor
Browser for CoreData stores in your app. Shows model scheme just like Xcode editor, allows to navigate data, follow relations, switching contexts and running custom fetch requests against any model / context.

#### Performance monitor
Displays real-time graphs of the CPU / Memory/ Network / Disk / Battery usage.

#### Logs monitor
Displays all logs generated by your app. We provide integration with popular logging framework [CocoaLumberjack](https://github.com/CocoaLumberjack/CocoaLumberjack), all your logs written with loggers from it will be displayed with respect to their logging levels.

#### Location monitor
Most of the apps are location-aware. Testing it requires changing locations yourself. In this case, location mocking is a real time saver. Just point to the location on the map and your app will change its geodata right away.

## Configure
AppSpector uses modules called monitors to track different app activities and gather stats.
We provide a bunch of monitors out of the box which could be used together or in any combinations.
To start AppSpector you need to build instance of `AppSpectorConfig` and provide your API key.
You can start exact monitors with:

```configWithAPIKey:(NSString *)apiKey monitorIDs:(NSSet <NSString *> *)monitorIDs``` 

Or start all available with:

```configWithAPIKey:(NSString *)apiKey```

Available monitors:

```
AS_SCREENSHOT_MONITOR
AS_SQLITE_MONITOR
AS_HTTP_MONITOR
AS_COREDATA_MONITOR
AS_PERFORMANCE_MONITOR
AS_LOG_MONITOR
AS_LOCATION_MONITOR
```



### Objective-C
<!-- integration-objc-example-start -->
Starting only selected monitors:
```objective-c
NSSet *monitorIDs = [NSSet setWithObjects:AS_HTTP_MONITOR, AS_LOG_MONITOR, nil];
AppSpectorConfig *config = [AppSpectorConfig configWithAPIKey:@"API_KEY" monitorIDs:monitorIDs];
[AppSpector runWithConfig:config];
```

Or all at once:
```
AppSpectorConfig *config = [AppSpectorConfig configWithAPIKey:@"API_KEY"];
[AppSpector runWithConfig:config];
```
<!-- integration-objc-example-end -->

### Swift
<!-- integration-swift-example-start -->
```swift
let config = AppSpectorConfig(apiKey: "API_KEY", monitorIDs: [AS_HTTP_MONITOR, AS_LOG_MONITOR])
AppSpector.run(with: config)
```
or to start all monitors:
```
let config = AppSpectorConfig(apiKey: "API_KEY")
AppSpector.run(with: config)
```
<!-- integration-swift-example-end -->

## Feedback
Let us know what do you think or what would you like to be improved: [info@appspector.com](mailto:info@appspector.com).
