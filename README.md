# RadixUI-Swift
> Radix-UI is an open source library optimized for fast development, easy maintenance, and accessibility.

[![Swift Version][swift-image]][swift-url]
[![License][license-image]][license-url]

Since [Radix-UI](https://www.radix-ui.com) developers said it is not available to Mobile Development (like SwiftUI) and never be ([reference](https://github.com/radix-ui/themes/issues/522)), I decided to make it ready for myself to use it because I just like it so much.
My inspiration for doing it is [Basics](https://swiftuibasics.com) website and the minimal and gorgeous design of Radix-UI.

## Installation

Add this project on your `Package.swift`

```swift
import PackageDescription

let package = Package(
    dependencies: [
        .package(url: "https://github.com/amirsaam/RadixUI-Swift.git", from: "0.8.00"),
    ]
)
```

## Usage example


Surely import the package
```swift
import RadixUI
```

Use colors as any other colors
```swift
Text("RadixUI-Swift")
  .foregroundColor(.crimson1)
```

In order to use your own custom color pallete head to [Radix Pallete Generator](https://www.radix-ui.com/colors/custom) and create your pallete and then use color hexes to have your own pallete with the following code:
```swift
public extension Color {
    static let colorExampleSolid = Color(lightHex: "lightSixDigitHex", darkHex: "darkSixDigitHex")
    static let colorExampleAlpha = Color(lightHex: "lightEightDigitHex", darkHex: "darkEightDigitHex")
}
```

Use icons in `Image` with bundle name completely customisable
```swift
Image("github-logo", bundle: .radixUI)
  .resizable()
  .aspectRatio(contentMode: .fit)
  .frame(width: anySize, height: anySize)
  .foregroundColor(.ruby9)
```
Or, make some custom extension to use `Label`
```swift
struct ResizeableBundledImage: View {

  let imageName: String
  let imageSize: CGFloat
  let bundle: Bundle

  var body: some View {
    Image(imageName, bundle: bundle)
      .resizable()
      .aspectRatio(contentMode: .fit)
      .frame(width: imageSize, height: imageSize)
  }
}

extension Label where Title == Text, Icon == ResizeableBundledImage {
  init(_ title: LocalizedStringKey, imageName: String, imageSize: CGFloat, bundle: Bundle) {
    let titleView: () -> Text = { Text(title) }
    let iconView: () -> ResizeableBundledImage = { ResizeableBundledImage(imageName: imageName, imageSize: imageSize, bundle: bundle) }
    self.init(title: titleView, icon: iconView)
  }
}
```
Apply RadixSwitch style to SwiftUI Toggles:
```swift
Toggle(isOn: $toggleBinding) {
    AnyLabel
}
.radixSwitch(onColor: .ruby9, offColor: .gray7, thumbColor: .ruby9)
// Or simply for Black and White
.radixSwitch()
```
For changing Segmented Picker of SwiftUI to match Radix style create an `init` in `@main` struct of the app or just apply such `init` in any view you want: 
```swift
@main
struct RadixApp: App {

  init() {
    RadixSegmentedPicker(
      backgroundColor: .ruby3,
      selectedColor: .ruby12,
      foregroundColor: .ruby4
    )
  }

  var body: some Scene {
    WindowGroup {
      ContentView()
    }
  }
}
```
Radix Shadows are available as `ViewModifier` in 6 level:
```swift
AnyView
.radixShadow1()
.radixShadow2()
.radixShadow3()
.radixShadow4()
.radixShadow5()
.radixShadow6()
```

## To Do

Any PRs are welcomed:
- [x] Add [Radix Colors](https://github.com/radix-ui/colors)
- [x] Add [Radix Icons](https://github.com/radix-ui/icons)
- [ ] Add [Radix Primitives](https://github.com/radix-ui/primitives) (WIP)
- [ ] Add [Radix Themes](https://github.com/radix-ui/themes) (WIP)
- [x] Make a macOS ready version
- [ ] Write Xcode Tests
- [ ] Make Pod
- [x] Deploy Github Action

## Dependencies 

- RadixUI-Swift has no dependency

## Meta

Amir Mohammadi – [@amirsaam](https://twitter.com/amirsaam) – amirsaam [at] me [dot] com

Distributed under the MIT license. See ``LICENSE`` for more information.

[https://github.com/amirsaam/RadixUI-Swift](https://github.com/amirsaam/RadixUI-Swift)

## Credits

- [@WorkOS](https://github.com/workos) for [Radix-UI](https://github.com/radix-ui)

[swift-image]:https://img.shields.io/badge/swift-5.4-orange.svg
[swift-url]: https://swift.org/
[license-image]: https://img.shields.io/badge/License-MIT-blue.svg
[license-url]: LICENSE
