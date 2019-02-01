# React Native Training

![](QQ20160705-3.png)

The videos are here \([YouTube](https://www.youtube.com/playlist?list=PLC_rYRxEnwQGLQqrHR0aho33U6DCeJamC), [YouKu](http://v.youku.com/v_show/id_XMTYzODIxMDA2MA==.html?spm=a2hzp.8253876.0.0&f=27615900) \(中文\)!

![](QQ20160727-3.png)

Please [leave a message](https://www.gitbook.com/book/unbug/react-native-training/discussions) or twitter [@unbug](https://twitter.com/unbug) for further inquiries. Any help will be appreciated :\)

# Table of contents

* [1 First look](https://github.com/unbug/react-native-train/blob/master/chapter1.md)
  * [1.1 Building an app in 5 minutes](https://github.com/unbug/react-native-train/blob/master/11_building_an_app_in_5_minutes.md)
  * [1.2 How it works](https://github.com/unbug/react-native-train/blob/master/12_how_it_works.md)
  * [1.3 Debug tools](https://github.com/unbug/react-native-train/blob/master/13_debug_tools.md)
  * [1.4 DOCs & APIs](https://github.com/unbug/react-native-train/blob/master/14_docs_%26_apis.md)
  * [1.5 Resources](https://github.com/unbug/react-native-train/blob/master/15_resources.md)
* [2 Components](https://github.com/unbug/react-native-train/blob/master/2_components.md)
  * [2.1 Render & JSX](https://github.com/unbug/react-native-train/blob/master/21_render_%26_jsx.md)
  * [2.2 View, Text, Image, etc](https://github.com/unbug/react-native-train/blob/master/25_view%2C_text%2C_image%2C_etc.md)
  * [2.3 Lifecyle](https://github.com/unbug/react-native-train/blob/master/23_lifecyle.md)
  * [2.4 Props & States](https://github.com/unbug/react-native-train/blob/master/23_states_%26_props.md)
  * 2.5 Events
  * 2.6 Resources
* 3 Styles
  * 3.1 Flexbox
  * 3.2 Absolute & Relative
  * 3.3 Size & Dimensions & onLayout
  * 3.4 Inheritance
  * 3.5 Resources
* 4 Architecture
  * 4.1 Redux
  * 4.2 react-redux
  * 4.3 Containers & Components
  * 4.4 Todo React Native App
  * 4.5 Naming convention
  * 4.6 Resources
* 5 Data
  * 5.1 Fetch
  * 5.2 Persistent
  * 5.3 Resources
* 6 Router
  * 6.1 Navigator
  * 6.2 Resources
* 7 Native Modules \(draft\)
  * 7.1 iOS
    * 7.1.1 JS call OC
    * 7.1.2 OC call JS
    * 7.1.3 Native View Component
* * 7.2 Android
    * 7.2.1 JS call Java
    * 7.2.2 Java call JS
    * 7.2.3 Native View Component
  * 7.3 Resources
* 8 Integration \(draft\)
  * 8.1 iOS
    * 8.1.1 Package
    * 8.1.2 Image
  * 8.2 Android
    * 8.2.1 Package
    * 8.2.2 Image
  * 8.3 Before publishing
  * 8.4 Resources
* 9 Hot Update \(draft\)
  * 9.1 iOS
  * 9.2 Android
  * 9.3 Resources
* 10 Performance \(draft\)
  * 10.1 shouldComponentUpdate
  * 10.2 Resources
* [Resources](https://github.com/unbug/react-native-train/blob/master/resources.md)

---

# 1 First Look

[Introducing React Native](https://facebook.github.io/react/blog/2015/03/26/introducing-react-native.html)

> What we really want is the user experience of the native mobile platforms, combined with the developer experience we have when building with React on the web.  
> With a bit of work, we can make it so the exact same React that's on GitHub can power truly native mobile applications. The only difference in the mobile environment is that instead of running React in the browser and rendering to divs and spans, we run it an embedded instance of JavaScriptCore inside our apps and render to higher-level platform-specific components.  
> It's worth noting that we're not chasing **“write once, run anywhere.”** Different platforms have different looks, feels, and capabilities, and as such, we should still be developing discrete apps for each platform, but the same set of engineers should be able to build applications for whatever platform they choose, without needing to learn a fundamentally different set of technologies for each. We call this approach **“learn once, write anywhere.”**

[Showcase](https://facebook.github.io/react-native/showcase.html)

![](QQ20160630-4.png)

# 1.1 Building an app in 5 minutes

1. Requirement follow [Getting Started ](http://facebook.github.io/react-native/releases/next/docs/getting-started.html)
2. Generate a new React Native project
   ```shell
   react-native init testRn
   ```
3. Build & run project
   ```shell
   react-native run-ios
   ```

   or open `testRn/ios/testRn.xcodeproj` and build with XCode's play button

![](QQ20160622-0.png)

or if the app already builded, start the webserver

```shell
npm start
//or
react-native start
```



# 1.2 How it works

1.[JavaScript bridge](https://www.infoq.com/articles/react-native-introduction)

![](21.jpg)

2.[React Native Packager](https://github.com/facebook/react-native/tree/master/packager)

![](Pasted Graphic.jpg)

# 1.3 Debug tools

1.[developer menu](https://facebook.github.io/react-native/docs/debugging.html)

![](QQ20160623-0.png)

2.Chrome Devtools

![](QQ20160623-2.png)  
3.log

```shell
console.log('some text');
console.dir({a:1, b:2, c:3});
debugger;//breaking point
```

4.[Atom](https://atom.io/) & [nuclide](https://nuclide.io/)

![](QQ20160623-3.png)

5.inspect

Open Atom [Command Palette package](https://atom.io/packages/command-palette) with `cmd-shift-p` and search "inspector", then click "Nuclide React Native Inspector:Show"

![](QQ20160624-0.png)

![](QQ20160623-4.png)

6.[Real device](https://facebook.github.io/react-native/docs/debugging.html#chrome-developer-tools)

6.1 Deploy to real device  
`project_name/ios/project_name/AppDelegate.m`

```c
  //jsCodeLocation = [NSURL URLWithString:@"http://localhost:8081/index.ios.bundle?platform=ios&dev=true"];

  /**
   * OPTION 2
   * Load from pre-bundled file on disk. The static bundle is automatically
   * generated by the "Bundle React Native code and images" build step when
   * running the project on an actual device or running the project on the
   * simulator in the "Release" build configuration.
   */

   jsCodeLocation = [[NSBundle mainBundle] URLForResource:@"main" withExtension:@"jsbundle"];
```

6.2 Debug in real device

1.`project_name/ios/project_name/AppDelegate.m`

```c
  jsCodeLocation = [NSURL URLWithString:@"http://172.28.0.230:8081/index.ios.bundle?platform=ios&dev=true"];
```

2.`node_modules/react-native/Libraries/WebSocket/RCTWebSocketExecutor.m`

```c
  if (!_url) {
    NSUserDefaults *standardDefaults = [NSUserDefaults standardUserDefaults];
    NSInteger port = [standardDefaults integerForKey:@"websocket-executor-port"] ?: 8081;
    NSString *URLString = [NSString stringWithFormat:@"http://172.28.0.230:%zd/debugger-proxy?role=client", port];
    _url = [RCTConvert NSURL:URLString];
  }
```

3.

![](QQ20160826-0.png)



---

## Created by [@unbug](https://twitter.com/unbug):

* [MIHTool - iOS Web Debugger Pro](https://www.mihtool.com): MIHTool helps Front-End Engineers to debug and optimize their webpages on iPad and iPhone.
* [Codelf - 变量命名神器](https://unbug.github.io/codelf/): Organize your GitHub stars and repositories. Search over projects from GitHub to find real-world usage variable names.
* [js-middleware](https://github.com/unbug/js-middleware): Powerful Javascript Middleware Pattern implementation, apply middleweares to any object. A painless solution to make codes as scalable and maintainable as ReduxJS and ExpressJS.
* [SAY NO TO SUICIDE PUBLIC LICENSE](https://github.com/unbug/snts): We've lost so many genius developers, who committed suicide, such as Aaron Hillel Swartz \(November 8, 1986 – January 11, 2013\). As a developer, the community needs you, the world needs you, please keep yourself alive.



