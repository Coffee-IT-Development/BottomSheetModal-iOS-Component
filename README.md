[![Coffee IT - iOS Aroma BottomSheet Component](Docs/Images/readme-cover.png)](https://coffeeit.nl/)

[![Swift Package Manager](https://img.shields.io/badge/Swift_Package_Manager-Compatible-brightgreen?style=flat-square)](https://img.shields.io/badge/Swift_Package_Manager-Compatible-brightgreen?style=flat-square)
[![Swift {swift_version}](https://img.shields.io/badge/Swift-5.6-brightgreen?style=flat-square)](https://img.shields.io/badge/Swift-5.6-brightgreen?style=flat-square)
[![iOS {ios_version}](https://img.shields.io/badge/iOS-v13+-brightgreen?style=flat-square)](https://img.shields.io/badge/iOS-v13+-brightgreen?style=flat-square)
[![Mirror Repository](https://img.shields.io/badge/Mirror-Repository-brightgreen?style=flat-square)](https://img.shields.io/badge/Mirror-Repository-brightgreen?style=flat-square)
[![License](https://img.shields.io/badge/License-MIT-brightgreen.svg?style=flat-square)](LICENSE.md)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-CoffeeIT-blue.svg?style=flat-square)](https://linkedin.com/company/coffee-it)
[![Facebook](https://img.shields.io/badge/Facebook-CoffeeITNL-blue.svg?style=flat-square)](https://www.facebook.com/CoffeeITNL/)
[![Instagram](https://img.shields.io/badge/Instagram-CoffeeITNL-blue.svg?style=flat-square)](https://www.instagram.com/coffeeitnl/)
[![Twitter](https://img.shields.io/badge/Twitter-CoffeeITNL-blue.svg?style=flat-square)](https://twitter.com/coffeeitnl)

A customizable BottomSheet that can be used from iOS 13 and up. Also has an Android counterpart.

<img src="Docs/Images/bottomsheet.gif" width="300">


## ⚡ Installation
This component requires minimum __iOS 13__.

### 🔨 SwiftPM
To install the Swift Package, go to Project > Package Dependencies > + > Search or Enter Package URL > Fill in:
```
https://github.com/Coffee-IT-Development/BottomSheet-iOS-Component
```

## 📖 Usage

Import CITBottomSheet and add a CITBottomSheetManager StateObject to the root of your app.
Then provide it to your root view as an environmentObject.

```swift
import CITBottomSheet
import SwiftUI

@main
struct CITBottomSheetExampleApp: App {
    @StateObject private var bottomSheetManager = CITBottomSheetManager()

    var body: some Scene {
        WindowGroup {
            CITBottomSheetExampleView()
                .environmentObject(bottomSheetManager)
        }
    }
}
```

In a view, retrieve your CITBottomSheetManager using @EnvironmentObject.
Then, use the bottomSheet modifier on your view like you would when using a normal sheet.
You can call bottomSheetManager.present() with your desired view content to make it appear.

```swift 
import CITBottomSheet
import SwiftUI

struct CITBottomSheetExampleView: View {
    @EnvironmentObject private var bottomSheetManager: CITBottomSheetManager
    
    private var config = CITBottomSheetConfig(
        backgroundColor: Color.white,
        height: .fixed(height: 300),
        cornerStyle: .roundedTopCorners
    )
    
    var body: some View {
        Button("Open Bottom Sheet") {
            bottomSheetManager.present() {
                VStack {
                    Text("Item 1")
                    Text("Item 2")
                    Text("Item 3")
                    Text("Item 4")
                    Text("Item 5")
                    Text("Item 6")
                }
            }
        }
        .bottomSheet(isPresented: bottomSheetManager.isPresenting, config: config, onDimiss: nil) {
            bottomSheetManager.sheet?.content
        }
    }

}
```


## ⚙️ Customization

```swift
/// Set background color
/// The app is responsible for setting the right background color for dark mode support
/// Required
/// No default value
let backgroundColor: Color

/// Heigth options:
/// - `auto` the bottom sheets calculates the height based on the view in it
/// - `fixed` the app sets the height
/// Required
/// No default value
let height: Height

/// Width options:
/// - `default` is full width of the view
/// - `fixed` the app sets the width
/// Optional
/// Default value: `default`
let width: Width

/// If set to true the bottom sheet is draggable to the top to expand the sheet
/// Optional
/// Default value = `false`
let isExpandable: Bool

/// If set to false the user cannot drag the sheet down to close it
/// Optional
/// Default value = `true`
let isDraggable: Bool

/// CornerStyle options:
/// - `roundedTopCorners` (only top corners, has default corner radius of 16)
/// - `roundedTopCornersCustom` (only top corners, set your own corner radius)
/// - `roundedAllCorners` (all corners, has default corner radius of 16)
/// - `roundedAllCornersCustom` (all corners, set your own corner radius)
/// - `square` (no corner radius)
/// Required
/// No default value
let cornerStyle: CornerStyle

/// Accessory options:
/// - `grabber`
/// - `closeButton` (which you need to give a `backgroundStyle` either `.dark` or `.light`)
/// Optional
/// Default value = `nil`
let accessory: Accessory?

/// OverlayStyle options:
/// - `default` black (60% opacity) overlay
/// - `custom` set your own overlay by specifying `color` and `opacity`
/// Optional
/// Default value = `default`
/// Could be set to `nil` for no overlay
let overlayStyle: OverlayStyle?

/// You set the `bottomPadding` to create a floating bottom sheet.
/// Optional
/// Default value = `.zero`
let bottomPadding: CGFloat
```

## 🔗 Related publications

- [BottomSheet for Android](https://github.com/Coffee-IT-Development/BottomSheet-Android-Component/)

Look at our other repositories on our [GitHub account](https://github.com/orgs/Coffee-IT-Development/repositories).

## ✏️ Changelog

All notable changes to this project will be documented in the [Changelog](CHANGELOG.md).
`CITBottomSheet` adheres to [Semantic Versioning](https://semver.org/).

## 📧 Contact

Do you have questions, ideas or need help? Send us an email at contact@coffeeit.nl.

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://global-uploads.webflow.com/605a171ee93af49275331843/623b23cdea80a92703e61b42_Logo_black_1.svg" width="100">
  <source media="(prefers-color-scheme: light)" srcset="https://coffeeit.nl/wp-content/uploads/2016/09/logo_dark_small_new.png" width="100">
  <img alt="CoffeeIT logo" src="https://coffeeit.nl/wp-content/uploads/2016/09/logo_dark_small_new.png" width="100">
</picture>

## ⚠️ License

Distributed under the MIT License. [See LICENSE](LICENSE.md) for more information.
