# iOS-Debug-Tools
A simple shake-gesture initiated UIAlertController Action Sheet that provides easy access for developers to submit bug reports (including screenshots and written messages) to Slack. Tools also supports [Facebook Tweaks](https://github.com/facebook/Tweaks)

![alt text](https://raw.githubusercontent.com/dennisfedorko/iOS-Debug-Tools/master/Tools-Menu.png "Tools Menu Screenshot")

# How To Use
*See demo project for example of how to use Tools*
1. Download the `Tools` folder and drag into project.
2. Add the following Objective-C import statements to your bridging header:
```swift
#import "FBTweak.h"
#import "FBTweakStore.h"
#import "FBTweakCategory.h"
#import "FBTweakCollection.h"
#import "FBTweakViewController.h"
#import "FBTweakShakeWindow.h"
```
3. Initialize Tools in your `AppDelegate.swift` file with a root view controller, Slack channel, Slack token, and Slack name for message reporter bot. Your Slack tokens and channel id can be found on the [Slack API Website](https://api.slack.com/web)
4. Activate the tools menu by shaking the iOS device either in the simulator or on your hardware and a UIAlertController Action Sheet should appear.
5. Use the menu options to submit a message, screenshot, or toggle [Facebook Tweaks](https://github.com/facebook/Tweaks)
6. Once you fill out the text you want submitted with your message/screenshot, hit submit on the bug submission view controller and your request will upload asynchronously to Slack.

# Example
Add the following Objective-C import statements to your bridging header:
```swift
#import "FBTweak.h"
#import "FBTweakStore.h"
#import "FBTweakCategory.h"
#import "FBTweakCollection.h"
#import "FBTweakViewController.h"
#import "FBTweakShakeWindow.h"
```
Set slack channel, token, and username in `AppDelegate.swift` and create var tools at the top of the app delegate class.
See demo `AppDelegate.swift` file for more info
```
var tools: Tools!

//example Slack info
let slackChannel = "ABC123"
let slackToken = "ABC123"
let slackUsername = "Feedback Reporter Bot"

```
Initialize Tools in your `AppDelegate.swift` *application didFinishLaunchingWithOptions* method
```swift
func application(application: UIApplication, didFinishLaunchingWithOptions launchOptions: [NSObject: AnyObject]?) -> Bool
{
    //instantiate window
    self.window = UIWindow(frame: UIScreen.mainScreen().bounds)
    self.window!.makeKeyAndVisible()
    self.window?.rootViewController = ViewController()

    //declaration of tools remains active in background while app runs
    tools = Tools(rootViewController: self.window!.rootViewController!, slackChannel: slackChannel, slackToken: slackToken, slackUsername: slackUsername)

    return true
}
```
After completing the above steps, you should now be able to shake your device and see the **Tools** menu appear. Happy Bug Reporting :)

# Requirements
Build currently supports the following configuration
- Swift 2.0+
- iOS 8.0+
- XCode 7.0
