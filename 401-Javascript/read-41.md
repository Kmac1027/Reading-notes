# Reading 41: React Native

## Getting Started with React Native

[Link to Article](https://reactnative.dev/docs/getting-started)

- With React, you can make components using either classes or functions. Originally, class components were the only components that could have state. But since the introduction of React's Hooks API, you can add state and more to function components.

## react native basics (Tutorial)

[Link to Article](https://reactnative.dev/docs/tutorial)

- React Native is like React, but it uses native components instead of web components as building blocks. So to understand the basic structure of a React Native app, you need to understand some of the basic React concepts, like JSX, components, state, and props. If you already know React, you still need to learn some React-Native-specific stuff, like the native components. This tutorial is aimed at all audiences, whether you have React experience or not.
- Your own components can also use props. This lets you make a single component that is used in many different places in your app, with slightly different properties in each place. Refer to props.{NAME} in your functional components or this.props.{NAME} in your class components.
- Unlike props that are read-only and should not be modified, the state allows React components to change their output over time in response to user actions, network responses and anything else.
- In a React component, the props are the variables that we pass from a parent component to a child component. Similarly, the state are also variables, with the difference that they are not passed as parameters, but rather that the component initializes and manages them internally.

## react native

[Link to Article](https://reactnative.dev/)

- React Native combines the best parts of native development with React, a best-in-class JavaScript library for building user interfaces.
- Many platforms, one React. Create platform-specific versions of components so a single codebase can share code across platforms. With React Native, one team can maintain two platforms and share a common technology—React.
- React Native lets you create truly native apps and doesn't compromise your users' experiences. It provides a core set of platform agnostic native components like View, Text, and Image that map directly to the platform’s native UI building blocks.
- React components wrap existing native code and interact with native APIs via React’s declarative UI paradigm and JavaScript. This enables native app development for whole new teams of developers, and can let existing native teams work much faster.

## Expo and Expo Snack

[Link to Site](https://expo.io/)
[Link to expo snack](https://snack.expo.io/)

## Ejecting

[Lin k to Article](https://docs.expo.io/expokit/eject/?redirected)

- ExpoKit is an Objective-C and Java library that allows you to use the Expo platform and your existing Expo project as part of a larger standard native project -- one that you would normally create using Xcode, Android Studio, or react-native init.
- Normally, Expo apps are written in pure JS and never "drop down" to the native iOS or Android layer. This is core to the Expo philosophy and it's part of what makes Expo fast and powerful to use. However, there are some cases where advanced developers need native capabilities outside of what Expo offers out-of-the-box. The most common situation is when a project requires a specific Native Module which is not supported by React Native Core or the Expo SDK.
- In this case, Expo allows you to eject your pure-JS project from the Expo iOS/Android clients, providing you with native projects that can be opened and built with Xcode and Android Studio. Those projects will have dependencies on ExpoKit, so everything you already built will keep working as it did before.
- We call this "ejecting" because you still depend on the Expo SDK, but your project no longer lives inside the standard Expo client. You control the native projects, including configuring and building them yourself.

### Should I eject to ExpoKit?

- Yes if:
  1. Your Expo project needs a native module that Expo doesn't currently support. We're always expanding the Expo SDK, so we hope this is never the case. But it happens, especially if your app has very specific and uncommon native demands.
- No if:
  1. All you need is to distribute your app in the iTunes Store or Google Play. Expo can build binaries for you in that case. If you eject, we can't automatically build for you any more.
  1. You are uncomfortable writing native code. Ejected apps will require you to manage Xcode and Android Studio projects.
  1. You enjoy the painless React Native upgrades that come with Expo. After your app is ejected, breaking changes in React Native will affect your project differently, and you may need to figure them out for your particular situation.
  1. You require Expo's push notification services. After ejecting, since Expo no longer manages your push credentials, you'll need to manage your own push notification pipeline.
  1. You rely on asking for help in the Expo community. In your native Xcode and Android Studio projects, you may encounter questions which are no longer within the realm of Expo.


[Back to code 401 notes](../401-Javascript.md)