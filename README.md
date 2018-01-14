
# react-native-launch-darkly

React Native wrapper over LaunchDarkly SDK's for iOS and Android.

[LaunchDarkly](https://launchdarkly.com)

[Native iOS SDK](https://github.com/launchdarkly/ios-client)

[Native Android SDK](https://github.com/launchdarkly/android-client)

## Getting started

`$ npm install launch-darkly-react-native --save`

or

``$ yarn add launch-darkly-react-native --save``

### Mostly automatic installation

`$ react-native link launch-darkly-react-native`

#### iOS:

1) In XCode in project navigator, develop RNLaunchDarkly.xcodeproj.
2) Drag and drop DarklyEventSource.framework, Pods_Darkly_iOS.framework and Darkly.framework to the Frameworks folder of your project.
3) Go to you project target and add DarklyEventSource.framework, Pods_Darkly_iOS.framework and Darkly.framework to Embedded Binaries

#### Android:

/!\ The Android project has not been updated from the original fork and has not been tested yet!

Add line bellow at the bottom of your app/build.gradle
  ```
  configurations.all { resolutionStrategy.force 'com.squareup.okhttp3:okhttp:3.4.1' }
  ```

### Manual installation


#### iOS

1. In XCode, in the project navigator, right click `Libraries` ➜ `Add Files to [your project's name]`
2. Go to `node_modules` ➜ `launch-darkly-react-native` and add `RNLaunchDarkly.xcodeproj`
3. In XCode, in the project navigator, select your project. Add `libRNLaunchDarkly.a` to your project's `Build Phases` ➜ `Link Binary With Libraries`
4. In XCode in project navigator, develop RNLaunchDarkly.xcodeproj.
5. Drag and drop DarklyEventSource.framework, Pods_Darkly_iOS.framework and Darkly.framework to the Frameworks folder of your project.
6. Go to you project target and add DarklyEventSource.framework, Pods_Darkly_iOS.framework and Darkly.framework to Embedded Binaries
7. Run your project (`Cmd+R`)<

#### Android

/!\ The Android project has not been updated from the original fork and has not been tested yet!

1. Open up `android/app/src/main/java/[...]/MainActivity.java`
  - Add `import com.reactlibrary.RNLaunchDarklyPackage;` to the imports at the top of the file
  - Add `new RNLaunchDarklyPackage()` to the list returned by the `getPackages()` method
2. Append the following lines to `android/settings.gradle`:
  	```
  	include ':react-native-launch-darkly'
  	project(':react-native-launch-darkly').projectDir = new File(rootProject.projectDir, 	'../node_modules/react-native-launch-darkly/android')
  	```
3. Insert the following lines inside the dependencies block in `android/app/build.gradle`:
  	```
      compile project(':react-native-launch-darkly')
  	```
4. Add line bellow at the bottom of your app/build.gradle
    ```
    configurations.all { resolutionStrategy.force 'com.squareup.okhttp3:okhttp:3.4.1' }
    ```


## Usage
```javascript
import LaunchDarkly from 'launch-darkly-react-native';

const user = {
  key: 'key',
  email: 'email@example.com', // optional
  firstName: 'firstname', // optional
  lastName: 'lastname', // optional
  isAnonymous: false, // optional
};

// init native SDK with api key and user object
LaunchDarkly.configure('apiKey', user);

// get boolean feature flag value
LaunchDarkly.boolVariation('featureFlagName', (showFeature) => {
  console.log('Show feature:', showFeature);
});

// get string feature flag value
LaunchDarkly.stringVariation('featureFlagName', 'fallback', (value) => {
  console.log('String value:', value);
});
```
