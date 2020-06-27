
# What's New in SwiftUI

## Apps and Scenes

Apps are just like views
    `var body: some Scene`
[AppEssentials in SwiftUI]() - More on SwiftUI Scenes

WindowGroup
    - iOS - single full screen window
    - WatchOS - single fulls creen window
    - tvOS - 
    - iPadOS - support multiple istances for free
    - macOS - get command+N new window for free

Settings
    - macOS - provices standard scene


DocumentGroup - Provides document functionality

    commands API - auto add menu items and hotkeys (go look at doc here!)

Related:

[AppEssentials in SwiftUI]() (More on SwiftUI Scenes)
[Document-based Apps in SwiftUI]

## Launch Screen

Launch Screen Info.plist Key
    Allows us to delete the launch screen storyboard

## Widget

Widget Protocol

```
struct MyWidget: Widget {
    var body: some WidgetConfiguration {
        // stuff
    }
}
```

## Lists and Collections

- improve perf
- children
- grids

### Children

List(_:children:content) - Folding lists

### Grids

Lazy

can make adaptive or fixed columns

**Fixed**
```swift
LazyVGrid(columns: [GridItem(.adaptive(minimum: 176))]) {
    //ForEach...
}
```

**Adaptive**
```swift
LazyVGrid(columns: Array(repeating: GridItem(), count: 4)) {
    //ForEach...
}
```

## Toolbars and Controls

### Toolbars

- both UINavigationBar and UIToolbar
- Label("", systemImage: "")

`.help("hint")`
    - a11y hint on iOS
    - help on hover macOS

How to control focus
    - See SwiftUI for tvOS (applied to watchOS too!!!)

### Controls

#### ProgressView

`ProgressView("label", value: percentComplete)`
`ProgressView()` - loading idcon

#### Guage
```swift
Guage(value: acidity, in: 3...10) {
    Label("Soil Acidity", systemIamge: "drop.fill")
        .foregroundColor(.green)
} currentValueLabel: {
    Text("\(acidity)")
} minimumValueLabel: {
    Text("3")
} maximumValueLabel: {
    Text("10")
}
```

## Effects and Animations

```swift
@Namespace
matchedGrometryEffect(id:ID,in:NameSpace)
```

Adaptive clipping based on parent
```
.clipShape(containerRelativeShape())
```

Custom fonts scroll with dynamic type

`@ScaledMetric` - scales a value based on dynamic type size

ex:
```swift
@ScaledMetric private var padding = 8.0
```

Tint can be applied to views!
- set a default, but you can override on a per-view basis

## Frameworks and Features

### Links

Link View Item
    - works for URL and universal links
```swift
Link(destination: URL) {
    //Content
}
```

Open URL from a closure:
```swift
@Environment(\.openURL) private var openURL

if let url = output.requestURL {
    openURL(url)
}
```

### UniformTypeIdentifiers

- Uniform way to look at content type
- Drag and drop uses `UniformTypeIdentifiers`

### New System Frameworks w/ SwiftUI Support

- AuthenticaionServices
- AVKit
- MapKit
- SceneKit
- SpriteKit
- QuickLook
- HomeKit
- ClockKit
- StoreKit
- WatchKit
