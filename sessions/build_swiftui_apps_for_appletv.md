# Building SwiftUI Apps for AppleTV

## Button Styles and Context Menus

CardButtonStyle
- raises when focused
- direction when dragging on remote
- `.buttonStyle(CardButtonStyle())`

ContextMenus
- invoked on long press
- add actions (buttons)
ex
```swift
.contextMenu {
    Button("Button 1", action: someAction)
    Button("Button 2", action: anotherAction)
}
```

## Managing Focus

The focusable modifier
- NOT meant for intrinsically focusable views (button, list, etc)


`isFocused` environment var
- return true if nearest focusable anscestor is focused

ex
```swift
struct DetailsView {
  @Environment(\.isFocused) var isFocused: Bool
  var body: some View {
      VSTack {
          Text(songName)
          Text(isFocused ? artistAndALbum : artistName)
      }
  }
}
```

DefaultFocus
- `prefersDefaultFocus` - allows setting of default focus
- `focusScope` - limit default focus
- `resetFocus` - environment variable that sets back to default (limited to namespace)
ex
```swift
@Namespace private var namespace
@State private var areCredentialsFilled: Bool
@Environment(\.resetFocus) var resetFocus

var body: some View {
    VStack {
        // If no credentials, focus here
        TextField("username", text: $userName)
            .preferesDefaultFocus(!areCredentialsFilled, in: namespace)
        SecureField("pw", text: $password)

        // Focus here if we have credentials
        Button("Log In", action: login)
            .preferesDefaultFocus(areCredentialsFilled, in: namespace)

        // clear everything and set default focus again
        Button("Clear", action: {
            username = ""
            pw = ""
            areCredentialsFilled = false
            resetFocus(in: namespace)
        })
    }
}
```

## Layouts

Grid Items can control:
    - size
    - layout
    - spacing

