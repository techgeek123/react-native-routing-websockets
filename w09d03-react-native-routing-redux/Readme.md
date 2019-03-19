# React Native Routing, Components and API, Redux

## Learning Competencies
by the end of this day you will be able to learn about

- Routing in React Native
- different Components and APIs in React Native
- using redux in React Native application

## Overview
## Routing in React Native

### 1. Install Router

Run the following command in terminal, from the project folder to install `react-native-rouuter-flux`

`npm i react-native-router-flux --save`

### 2. Create a root component

Since we want our router to handle the entire application, we will add it in **index.ios.js**. For Android, you can do the same in **index.android.js**.

```js
index.ios.js && index.android.js

import React, { Component } from 'react';
import { AppRegistry, View } from 'react-native';
import Routes from './src/components/routes/Routes.js'

class reactTutorialApp extends Component {
   render() {
      return (
         <Routes />
      )
   }
}
export default reactTutorialApp

AppRegistry.registerComponent('reactTutorialApp', () ⇒ reactTutorialApp)
```

### 3. Add Router

Now we will create the **Routes** component inside the components folder. It will return **Router** with several **scenes**.

Each **Scene** will need `key`, `component` and `title`. `Router` uses the `key` property to switch between `scenes`, `component` will be rendered on screen and the `title` will be shown in the navigation bar.

We can also set the initial property to the scene that is to be rendered initially.

```js
src/components/routes/Routes.js

import React from 'react'
import { Router, Scene } from 'react-native-router-flux'
import Home from '../home/Home.js'
import About from '../about/About.js'

const Routes = () ⇒ (
   <Router>
      <Scene key = "root">
         <Scene key = "home" component = {Home} title = "Home" initial = {true} />
         <Scene key = "about" component = {About} title = "About" />
      </Scene>
   </Router>
)
export default Routes
```

### 4. Create components

Create **Home** and **About** components. 

We will add the **goToAbout** and the **goToHome** functions to switch between scenes.

```js
src/components/home/Home.js

import React from 'react'
import { TouchableOpacity, Text } from 'react-native';
import { Actions } from 'react-native-router-flux';

const Home = () ⇒ {
   const goToAbout = () ⇒ {
      Actions.about()
   }
   return (
      <TouchableOpacity style = {{ margin: 128 }} onPress = {goToAbout}>
         <Text>This is HOME!</Text>
      </TouchableOpacity>
   )
}
export default Home
```

```js
src/components/home/About.js

import React from 'react'
import { TouchableOpacity, Text } from 'react-native'
import { Actions } from 'react-native-router-flux'

const About = () ⇒ {
   const goToHome = () ⇒ {
      Actions.home()
   } 
   return (
      <TouchableOpacity style = {{ margin: 128 }} onPress = {goToHome}>
         <Text>This is ABOUT</Text>
      </TouchableOpacity>
   )
}
export default About
```

Read about [Handling Touches](https://facebook.github.io/react-native/docs/handling-touches.html) to know about `TouchableOpacity`

## Components and API

### View

View is the most common element in React Native. You can consider it as an equivalent of the div element used in web development.

The View can be assumed as a default element in React Native.

```js
src/components/home/Home.js

import React, { Component } from 'react'
import { View, Text } from 'react-native'

const Home = () ⇒ {
   return (
      <View>
         <View>
            <Text>This is my text</Text>
         </View>
      <View>
   )
}
export default Home
```

### Webview

Webview is used when you want to render web page to your mobile app inline.

#### Usage

The HomeContainer will be a container component.
```js
src/components/home/HomeContainer.js

import React, { Component } from 'react'
import WebViewExample from './WebViewExample'

const Home = () ⇒ {
   return (
      <WebViewExample/>
   )
}
export default Home;
```

create a new file called `WebViewExample.js` inside the `src/components/home` folder

```js
src/components/home/WebViewExample.js

import React, { Component } from 'react'

import {
   View,
   WebView,
   StyleSheet
} 
from 'react-native'

const WebViewExample = () ⇒ {
   return (
      <View style = {styles.container}>
         <WebView
            source = {{ uri: 
               'https://www.google.com/?gws_rd=cr,ssl&ei=SICcV9_EFqqk6ASA3ZaABA#q=tutorialspoint' }}
         />
      </View>
   )
}
export default WebViewExample;

const styles = StyleSheet.create({
   container: {
      height: 350,
   }
})
```

### Alert

```js
src/components/home/Home.js

import React from 'react'
import AlertExample from './AlertExample.js'

const Home = () ⇒ {
   return (
      <AlertExample />
   )
}
export default Home
```

We will create a button for triggering the showAlert function.

```js
src/components/home/AlertExample.js

import React from 'react'
import { Alert, Text, TouchableOpacity, StyleSheet } from 'react-native'

const AlertExample = () ⇒ {
   const showAlert = () ⇒ {
      Alert.alert(
         'You need to...'
      )
   }
   return (
      <TouchableOpacity onPress = {showAlert} style = {styles.button}>
         <Text>Alert</Text>
      </TouchableOpacity>
   )
}
export default AlertExample

const styles = StyleSheet.create ({
   button: {
      backgroundColor: '#4ba37b',
      width: 100,
      borderRadius: 50,
      alignItems: 'center',
      marginTop: 100
   }
})
```

### CameraRoll

The Camera module we want to use in this example is external so we need to install it first. We can do it from the terminal.

`npm i react-native-camera@0.6`

**takePicture** method will return a promise and path of the picture.

```js
src/components/home/AsyncStorageExample.js

import React, { Component } from 'react';

import {
   StyleSheet,
   Text,
   View
}
from 'react-native';
import Camera from 'react-native-camera';

class Inputs extends Component {
   takePicture = () ⇒ {
      const options = {};
      this.camera.capture({ metadata: options })
      .then((data) ⇒ console.log(data))
      .catch(err ⇒ console.error(err));
   }
   render() {
      return (
         <View style = {styles.container}>
            <Camera
               ref = {(cam) ⇒ {
                  this.camera = cam;
               }}
               style = {styles.preview}
               aspect = {Camera.constants.Aspect.fill}>
            </Camera>
            <Text style = {styles.capture} onPress = {this.takePicture}>CAPTURE</Text>
         </View>
      );
   }
}
export default Inputs

const styles = StyleSheet.create({
   container: {
      flex: 1,
   },
   preview: {
      flex: 1,
      justifyContent: 'flex-end',
      alignItems: 'center'
   },
   capture: {
      fontSize: 30,
      color: 'red',
      alignSelf: 'center',
   }
});
```
## Exploration

- Read more about [components and APIs](https://facebook.github.io/react-native/docs/components-and-apis.html)
- Understand the basic Components of React [here](https://habiletechnologies.com/blog/understanding-the-basic-components-of-react-native/)
- [React native & Redux](https://medium.com/@jonlebensold/getting-started-with-react-native-redux-2b01408c0053)
- React Native with Redux for [Beginners](https://medium.com/@imranhishaam/react-native-with-redux-for-beginners-6281959a2899)
