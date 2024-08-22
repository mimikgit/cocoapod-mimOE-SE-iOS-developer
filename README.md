# ``mimOE-SE-iOS``

mimik Client Library for iOS provides a programmatic way to work with the mimOE Runtime to access information about the mobile device on which the application is running.

@Metadata {
    @CallToAction(purpose: link, url: "https://github.com/mimikgit/cocoapod-mimOE-SE-iOS")
    @PageKind(article)
    @PageColor(orange)
}


## Overview

A Cloud-native Operating Environment that accelerates the integration of AI agents into solutions by bringing advanced capabilities directly to endpoint devices.

The **mimik iOS suite** consists of these individual cocoapod components:

    - mimOE-SE-iOS (or mimOE-SE-iOS-developer)
    - EdgeCore
    - EdgeUser

By leveraging the **`EdgeCore cocoapod`**, developers can build applications compatible with the mimOE Runtime.

Additionally, this component provides utility APIs that help developers with core operations such as Authentication, mimOE Runtime Setup, deployment of edge microservices and handling of network calls.

Furthermore, the **`mimOE-SE-iOS-developer (or mimOE-SE-iOS for enterprise projects) cocoapod`** provides mimOE Runtime lifecycle control API, as well as vendoring the actual mimOE Runtime binary into the iOS project.

Expanding the client library ecosystem is the **`EdgeService` cocoapod**, providing API for integrating mimik edge and backend microservices.


## Supported Platforms, Targets
* `iOS Devices running iOS 15+`
* `iOS Simulators running iOS 15+`
* `iOS Mac Catalyst running macOS 12.0`


## Requirements
```
iOS 15.0+
```

## Installation

To install `EdgeCore` and `mimOE-SE-iOS-developer (or mimOE-SE-iOS for enterprise solutions)` cocoapods simply add the following lines to your Podfile:

> **_NOTE:_** Developers wanting to use their **developer edge license** from [mimik developer console](https://developer.mimik.com/console) should specify [mimOE-SE-iOS-developer](https://github.com/mimikgit/cocoapod-mimOE-SE-iOS-developer) cocoapod in their `Podfile`.

> **_NOTE:_** Enterprise project developers should specify [mimOE-SE-iOS](https://github.com/mimikgit/cocoapod-mimOE-SE-iOS) cocoapod in their `Podfile` and use the **full edge license** they received from [mimik support](https://developer.mimik.com/support/).


```swift
platform :ios, '15.0'
source 'https://github.com/CocoaPods/Specs.git'
source 'https://github.com/mimikgit/cocoapod-edge-specs.git'

use_frameworks!
inhibit_all_warnings!

def mimik
  pod 'EdgeCore'
  pod 'mimOE-SE-iOS-developer'
  ### or pod 'mimOE-SE-iOS' (for enterprise projects, see the two notes above)
end

target '{target}' do
  mimik()
end

post_install do |installer|
  installer.pods_project.targets.each do |target|
    target.build_configurations.each do |config|
      config.build_settings['ENABLE_BITCODE'] = 'NO'
      config.build_settings['VALID_ARCHS'] = '$(ARCHS_STANDARD_64_BIT)'
      config.build_settings['IPHONEOS_DEPLOYMENT_TARGET'] = '15.0'
      config.build_settings['BUILD_LIBRARY_FOR_DISTRIBUTION'] = 'YES'
    end
  end
end
```

## Tutorials

After installation, try the following tutorials:

- [Integrating the mimik Client Library into an iOS project](https://devdocs.mimik.com/tutorials/11-index)
- [Working with mimOE in an iOS project](https://devdocs.mimik.com/tutorials/12-index)
- [Working with edge microservices in an iOS project](https://devdocs.mimik.com/tutorials/13-index)
- [Creating a Simple iOS Application that Uses an edge microservice](https://devdocs.mimik.com/tutorials/10-index)


## Documentation

`EdgeCore/EdgeClient` API reference documentation can be found  [online](https://mimikgit.github.io/cocoapod-EdgeCore/documentation/edgecore/edgeclient). Alternatively a docc archive file can be downloaded as a [zip file](https://github.com/mimikgit/cocoapod-EdgeCore/tree/main/EdgeCore.doccarchive.zip) and opened locally in Xcode.

`EdgeEngineClient` platform protocol API reference documentation can also be found [online](https://mimikgit.github.io/cocoapod-EdgeCore/documentation/edgecore/edgeengineclient).

`EdgeService` API reference documentation is also [online](https://mimikgit.github.io/cocoapod-EdgeService/documentation/).

## mimik client libraries

Explore all mimik client libraries [available on Github](https://github.com/search?q=cocoapod-Edge).
 
Cocoapod individual pods:
 
* [EdgeCore](https://github.com/mimikgit/cocoapod-EdgeCore)
* [mimOE-SE-iOS-developer](https://github.com/mimikgit/cocoapod-mimOE-SE-iOS-developer)
* [mimOE-SE-iOS](https://github.com/mimikgit/cocoapod-mimOE-SE-iOS)
* [EdgeService](https://github.com/mimikgit/cocoapod-EdgeService)


## Author

[mimik Technology, Inc.](https://mimik.com)

More details about how the mimOE platform revolutionizes computing with the hybrid-cloud approach are at [mimik Developer Documentation](https://devdocs.mimik.com).


## License

Developers can get their developer edge license by following this [tutorial](https://devdocs.mimik.com/tutorials/02-index).

For details about a full edge license please contact [mimik support](https://mimik.com/contact-us/).
