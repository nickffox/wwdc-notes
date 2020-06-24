# Build Complications in SwiftUI

Non-interactive

## New API

Templates in various sizes/shapes/positions for:
- gauge
- graphic/text
- SwiftUI view

Text updates based on face

DateFormats can autoupdate UI
- relative
- timer
- offset

### ProgressView

Styles
- circular
- linear

Supports
- label tint

### Gauge

Styles
- circular
- linear

Supports
- label
- minLabel
- maxLabel
- tint

## Watch Face Tinting

### Desaturated 
- is the default
- be careful with colors

### Color Opacity
- need to identify 2 distinct layers
- coloring is face-dependent so test in previews

Indicating foreground layer:
```swift
var body: some View {
    ZStack {
        Circle()
            .fill(Color.blue)
        Image("apple")
            .foregroundColor(.yellow)
            .complicationForeground() // tells us the image is the foreground
    }
}
```

### Advanced


#### ComplicationRenderingMode

`fullColor` or `tinted`

Use environment variable to access:

```swift
@Environment(\.complicationRenderingMode) var renderingMode
var body: some View {
    ZStack {
        switch renderingMode {
        case .fullColor:
            Circle()
                .fill(Color.blue)
        case .tinted:
            Circle()
                .fill(LinearGradient(...))
        }
        
        Image("apple")
            .foregroundColor(.yellow)
            .complicationForeground() // tells us the image is the foreground
    }
}
```

## Best Practices

- Not interactive
- SwiftUI animations not supported
- Pay attention to perf and watch out for runtime warnings
- Use default font sizes
- be aware of masks (if you use safe area this is handled for you)
