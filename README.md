# ``mimOE-SE-iOS-developer``

mimik Client Library for iOS provides a programmatic way to work with the mim OE (edgeEngine) Runtime to access information about the mobile device on which the application is running.

@Metadata {
    @CallToAction(purpose: link, url: "https://github.com/mimikgit/cocoapod-mimOE-SE-iOS-developer)
    @PageKind(article)
    @PageColor(orange)
}


## Overview

The purpose of the **mimik Client Library for iOS** is to provide a programmatic way to work with the mim OE (edgeEngine) Runtime, access information about its mobile device clusters, use on-device light-weight RESTful API edge microservices and optionally integrate with mimik ai components.

The **mimik Client Library for iOS** consists of the following cocoapod components:

    - EdgeCore
    - mimOE-SE-iOS-developer (for developer projects) 
    - mimOE-SE-iOS (for enterprise projects) 

These components provide various APIs that help developers with the core operations such as mim OE (edgeEngine) Runtime setup, developer authentication, deployment of edge microservices, as well as optionally integrating with [mimik ai components](https://devdocs.mimik.com/tutorials/02-submenu/02-submenu/01-index).

Generally speaking, developers only need to add the **`mimOE-SE-iOS-developer (for developer projects)`** or **`mimOE-SE-iOS (for enterprise projects)`** cocoapod to their project.

Expanding the client library ecosystem is an optional **`EdgeService` cocoapod**, providing API for integrating additional mimik edge and backend microservices.


## Supported Platforms, Targets
* `iOS Devices running iOS 15+`
* `iOS Simulators running iOS 15+`
* `iOS Mac Catalyst running macOS 12.0`


## Requirements
```
iOS 15.0+
```

## Installation

To get started simply add **`EdgeCore`** and **`mimOE-SE-iOS-developer`** cocoapod to your Podfile:


```swift
platform :ios, '15.0'
source 'https://github.com/CocoaPods/Specs.git'
source 'https://github.com/mimikgit/cocoapod-edge-specs.git'

use_frameworks!
inhibit_all_warnings!

def mimik
  pod 'EdgeCore'
  pod 'mimOE-SE-iOS-developer'
  ### or pod 'mimOE-SE-iOS' (for enterprise projects, see the notes above)
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

> **_NOTE:_** Developers should get their **developer edge license** for using [mimOE-SE-iOS-developer](https://github.com/mimikgit/cocoapod-mimOE-SE-iOS-developer) at the [mimik developer console](https://developer.mimik.com/console).

> **_NOTE:_** Enterprise project developers should get their **enterprise edge license** for using [mimOE-SE-iOS](https://github.com/mimikgit/cocoapod-mimOE-SE-iOS) from [mimik support](https://developer.mimik.com/support/).


## Documentation

`EdgeCore/EdgeClient` API reference documentation can be found  [online](https://mimikgit.github.io/cocoapod-EdgeCore/documentation/edgecore/edgeclient). Alternatively a docc archive file can be downloaded as a [zip file](https://github.com/mimikgit/cocoapod-EdgeCore/tree/main/EdgeCore.doccarchive.zip) and opened locally in Xcode.

`EdgeEngineClient` platform protocol API reference documentation can also be found [online](https://mimikgit.github.io/cocoapod-EdgeCore/documentation/edgecore/edgeengineclient).

`EdgeService` API reference documentation is also [online](https://mimikgit.github.io/cocoapod-EdgeService/documentation/edgeservice/).


## Tutorials

After installation, try the following tutorials:

- [Understanding the mimik Client Library for iOS](https://devdocs.mimik.com/key-concepts/10-index).
- [Creating a Simple iOS Application that Uses an edge microservice](https://devdocs.mimik.com/tutorials/01-submenu/02-submenu/01-index).
- [Integrating the mimik Client Library into an iOS project](https://devdocs.mimik.com/tutorials/01-submenu/02-submenu/02-index).
- [Working with mimOE in an iOS project](https://devdocs.mimik.com/tutorials/01-submenu/02-submenu/03-index).
- [Working with edge microservices in an iOS project](https://devdocs.mimik.com/tutorials/01-submenu/02-submenu/04-index).


## mimik Client Library cocoapods

* [EdgeCore](https://github.com/mimikgit/cocoapod-EdgeCore)
* [mimOE-SE-iOS-developer](https://github.com/mimikgit/cocoapod-mimOE-SE-iOS-developer)
* [mimOE-SE-iOS](https://github.com/mimikgit/cocoapod-mimOE-SE-iOS)
* [EdgeService](https://github.com/mimikgit/cocoapod-EdgeService)


## Author

[mimik Technology, Inc.](https://mimik.com)

More details about how the edgeEngine platform revolutionizes computing with the hybrid-cloud approach are at [mimik Developer Documentation](https://devdocs.mimik.com).


## License

Developers can get their developer edge license by following this [tutorial](https://devdocs.mimik.com/tutorials/01-submenu/02-submenu/03-index).

For details about an enterprise edge license please contact [mimik support](https://mimik.com/contact-us/).
