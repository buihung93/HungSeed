This Seed contain:
- React Native 0.57.4
- ES7
- axios
- react-navigation 2.17.0
- react-native-vector-icons
- prop-types
- eslint-config-airbnb
- react-native-vector-icons
- react-native-smart-splash-screen
- CodePush (remember to add deploy key in Info.plist and MainApplication.java)

- SET UP:

run `yarn`

Make sure all Facebook SDK is presend in Documents folder (follow install step provide by FB)



if build fail in Xcode then do follow:


IF Xcode 10: Build input file double-conversion:
To solve it I ran the following commands:

$ cd node_modules/react-native/scripts && ./ios-install-third-party.sh && cd ../../../
$ cd node_modules/react-native/third-party/glog-0.3.5/ && ../../scripts/ios-configure-glog.sh && cd ../../../../

Check list of App:
`code-push app ls`

Generate the update contents (JS bundle and assets) that will be released to the CodePush server:
`react-native bundle --platform android --entry-file index.js --bundle-output ./CodePush/main.jsbundle --assets-dest ./CodePush`

Release it!
Android: `code-push release-react AppNameAndroid android`
iOS: `code-push release-react AppNameIOS ios`



in RCTLinkingManager.h

`
/**
 * Copyright (c) 2015-present, Facebook, Inc.
 *
 * This source code is licensed under the MIT license found in the
 * LICENSE file in the root directory of this source tree.
 */

#import <UIKit/UIKit.h>

#import <React/RCTEventEmitter.h>

@interface RCTLinkingManager : RCTEventEmitter

+ (BOOL)application:(nullable UIApplication *)app
            openURL:(nullable NSURL *)URL
            options:(nullable NSDictionary<UIApplicationOpenURLOptionsKey,id> *)options;

+ (BOOL)application:(nullable UIApplication *)application
            openURL:(nullable NSURL *)URL
  sourceApplication:(nullable NSString *)sourceApplication
         annotation:(nullable id)annotation;

+ (BOOL)application:(nullable UIApplication *)application
continueUserActivity:(nullable NSUserActivity *)userActivity
  restorationHandler:(nullable void (^)(NSArray * __nullable))restorationHandler;

@end
`