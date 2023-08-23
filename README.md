# AviorMediaFeatures
A some features to create react native apps faster.

# Headers
- [Snackbar](#snackbar)
- [UXCAM](#uxcam)
- [Firebase](#firebase)
- [Webview](#webview)
- [Notifee](#notifee)
- [Slider](#svg)
- [Icons](#icons)
- [Idfaa](#idfaa)
- [Navigation](#navigation)
- [Styles](#styles)


# Color Picker
Visit [ImageColorPicker](https://imagecolorpicker.online/)

## Packages

### {#snackbar}
SnackBar 

```bash
npm i react-native-snackbar
```

```javascript
Snackbar.show({
  text: 'Hello world',
  duration: Snackbar.LENGTH_INDEFINITE,
  action: {
    text: 'UNDO',
    textColor: 'green',
    onPress: () => { /* Do something. */ },
  },
});
```

[NPM SnackBar](https://www.npmjs.com/package/react-native-snackbar)


### UXCAM {#uxcam}
Install UXCAM: 
```bash
npm install react-native-ux-cam
```
Add imports and configuration in `App.js`:
```javascript
import RNUxcam from 'react-native-ux-cam';
RNUxcam.optIntoSchematicRecordings();
const configuration = {
    userAppKey: 'YOUR_API_KEY',
    enableAutomaticScreenNameTagging: false,
    enableImprovedScreenCapture: true
};
RNUxcam.startWithConfiguration(configuration);
```

### Firebase {#firebase}
Install Firebase packages:
```bash
npm install @react-native-firebase/app @react-native-firebase/messaging
```
Add this code `to android/build.gradle`
```gradle
classpath 'com.google.gms:google-services:4.3.15'
```
Add this code to `android/app/build.gradle`:
```gradle
apply plugin: 'com.google.gms.google-services'
```
Add Google services configuration (google-services.json) to `android/app/build.gradle`:


### WebView {#webview}
Install WebView:
```bash
npm install react-native-webview
```

```js
import React from 'react'
import { ShouldStartLoadRequest } from 'react-native-webview/lib/WebViewTypes';
import WebView from 'react-native-webview';

export default function Crita({navigation, route}:any) {
  const url = route.params.url;
  
  const handleNavigations = (event: ShouldStartLoadRequest) => {
    navigation.replace("SET NAME FROM NAVIGATION", {url : event.url});
    return false;
  };
  console.log(route.params.url);
  return (
    <WebView
          cacheEnabled={false}
          cacheMode={'LOAD_NO_CACHE'}
          onShouldStartLoadWithRequest={handleNavigations}
          setSupportMultipleWindows={false}
          source={{ uri: url }}/>
  );
}
```

### Notifee {#notifee}
Install Notifee:
```bash
npm install @notifee/react-native
```

Add code
```js
import messaging from '@react-native-firebase/messaging';
import notifee from '@notifee/react-native';
```
```js
const handleMessages = async () => {
  const channelId = await notifee.createChannel({
    id: 'default',
    name: 'Default Channel',
  });

  messaging().onMessage(async remoteMessage => {
    if (remoteMessage.notification == null)
      return;
    await notifee.displayNotification({
      title: remoteMessage.notification.title,
      body: remoteMessage.notification.body,
      android: {
        channelId,
        smallIcon: remoteMessage.notification.icon,
        pressAction: {
          id: 'default',
        },
      }
    });
  });
}

React.useEffect(() => { handleMessages() }, []);
```


### Localize {#localize}
Install Localize:
```bash
npm install react-native-localize
```

### Svg {#svg}
Install SVG:
```bash
npm install react-native-svg
```
https://react-svgr.com/playground/?native=true


### Icons {#icons}
Find icons at:
- [UXWing](https://uxwing.com/no-wifi-icon/)
- [Icons8](https://icons8.com/icons/set/loading)
- [OnlineGIFTools](https://onlinegiftools.com/change-gif-background-color)

### Idfaa Advertising Id {#idfaa}
Install Idfaa Advertising Id:
```bash
npm install @sparkfabrik/react-native-idfa-aaid
```

### NetInfo {#netinfo}
Install NetInfo:
```bash
npm install @react-native-community/netinfo
```

### Swiper/Slider {#slider}
Install Swiper/Slider:
```bash
npm install react-native-swiper-flatlist
```

## Navigation {#navigation}

```js
{navigation, route}:any
```

### React Navigation
Install React Navigation packages:
```bash
npm install @react-navigation/native
npm install react-native-screens react-native-safe-area-context
```

### Navigation Stack
Install Navigation Stack:
```bash
npm install @react-navigation/stack
npm install react-native-gesture-handler
```

### Navigation Drawer
Install Navigation Drawer:
```bash
npm install @react-navigation/drawer
npm install react-native-gesture-handler react-native-reanimated
```
Remember to add this to the top of `App.js` or `index.js`:
```javascript
import 'react-native-gesture-handler';
```

Add import
```js
import { NavigationContainer} from '@react-navigation/native';
import { createStackNavigator } from '@react-navigation/stack';
```

Create Stack
```js
const Stack = createStackNavigator();
```

Using
```js
  const options = {
    headerShown:false,
  };

 <NavigationContainer>
      <Stack.Navigator>
        <Stack.Screen name='Navigator' component={Navigator} options={options} />
        <Stack.Screen name='Menu' component={Menu} options={options} />
    </Stack.Navigator>
  </NavigationContainer>
```

## Styles {#styles}
```js
import { StyleSheet } from "react-native"

export const primary  = "#00a500"
export const second = "#eee"

export const  styles = StyleSheet.create({
    text : {
        color: primary,
        fontSize: 14,
        lineHeight: 25,
    },
    header: {
        color: primary,
        fontSize: 16,
        fontWeight: 'bold',
        textAlign: 'center',
        lineHeight: 25,
    },
    subHeader: {
        color: primary,
        fontSize: 14,
        fontWeight: 'bold',
        lineHeight: 25,
    },
    _scrollView: {
        paddingTop: 10,
        paddingHorizontal: 10,
        height: '100%'
    },
});
```
```

















```
