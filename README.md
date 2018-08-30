# React Navigation [![CircleCI](https://circleci.com/gh/react-community/react-navigation/tree/master.svg?style=shield&circle-token=622fcb1d78413084c2f44699ed2104246a177485)](https://circleci.com/gh/react-community/react-navigation/tree/master) [![npm version](https://badge.fury.io/js/react-navigation.svg)](https://badge.fury.io/js/react-navigation) [![codecov](https://codecov.io/gh/react-community/react-navigation/branch/master/graph/badge.svg)](https://codecov.io/gh/react-community/react-navigation)


*Learn once, navigate anywhere.*

Browse the docs on [reactnavigation.org](https://reactnavigation.org/) or try it out on [our expo demo](https://exp.host/@react-navigation/NavigationPlayground).

## Motivation

React Navigation is born from the React Native community's need for an
extensible yet easy-to-use navigation solution. It replaces and improves
upon several navigation libraries in the ecosystem, including Ex-Navigation,
React Native's Navigator and NavigationExperimental components. React
Navigation can also be used across React and React Native projects allowing
for a higher degree of shared code.

Once stable, NavigationExperimental will be deprecated in favor of React
Navigation. React Navigation is a collaboration between people from
Facebook, Exponent and the React community at large.

## [Getting started](https://reactnavigation.org/docs/intro/)

1. Create a new React Native App
  ```
  react-native init SimpleApp
  cd SimpleApp
  ```

2. Install the latest version of react-navigation from npm
  ```
  yarn add react-navigation
  ```
  or
  ```
  npm install --save react-navigation
  ```

3. Run the new app
  ```
  react-native run-android # or:
  react-native run-ios
  ```

## Advanced guide

- [Redux integration](https://reactnavigation.org/docs/guides/redux)
- [Web integration](https://reactnavigation.org/docs/guides/web)
- [Deep linking](https://reactnavigation.org/docs/guides/linking)
- [Contributors guide](https://reactnavigation.org/docs/guides/contributors)

## React Navigation API

- [Navigators](https://reactnavigation.org/docs/navigators/)
- [Routers](https://reactnavigation.org/docs/routers/)
- [Views](https://reactnavigation.org/docs/views/)

## 2017-10-18 fix bug

Update StackRouter.js
对于 StackNavigation 的导航功能，如果点击多次 则会执行多次 类似于 this.props.navigation.navigate('LectureList'); 
会压入栈多个相同的页。
修改位置是： StackRouter.js  No.182，插入  

        if(state.routes.length > 0){
          if(state.routes[state.routes.length - 1].routeName == route.routeName){
            return state;
          }
        }
 这样就可以解决 多次压入同一个页的问题了
