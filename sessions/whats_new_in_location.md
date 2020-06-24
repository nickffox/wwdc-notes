# What's New in Location

## Location Authorization

Option to share "Precise" location
- setting on top of "when you have access

2x dimensions:

         |
accuracy |
         |_________
            when

```swift
//Replaced 
`class func authorizationStatus() -> CLLauthorizationStatus`
// with
let authorizationStatus: CLAuthorizationStatus { get }

// new
let accuracyAuthorization: CLAccuracyAuthorization { get }
CLAccuracyAuthorization { 
    case full
    case reduced
}
```
CLLocationManagerDelegate changes:
```swift
// deprecated
optional func locationManager(_ manager: CLLocationManager, didChangeAuthorizationStatus: CLAuthorizationStatus)
// for
optional func locationManagerDidChangeAuthorization(_ manager: CLLocationManager)
```

Reduced Accuracy Location Delivered
- standard delegate method
- 4x per hour
- treat it as "containing" the users true location

Referece [Designing for Location Privacy](https://developer.apple.com/videos/play/wwdc2020/10162)

Consider indicating that precise location is off (maps banner as an example)

Asking for Full Accuracy
- send to settings (probably bad)
- temporarily grant (new CLLocationManager API)


### Temporary Full Auth

Behavior is similiar to "Allow Once" from iOS permissions

Example:
```swift
locationManager.requestTemporaryFullAccuracyAuthorization(withPurposeKey: "someKey") { granted in
}
```
- Key must be in `NSLocationTemporaryUsageDescriptionDictionary` in info.plist
- Can support many keys for specific uses


### Background Location Updates

Region monitoring is disabled under reduced accuracy

### Manually set Reduced Accuracy 

On CLLocationManager:
`locationManager.desiredAccuracy = kCLLocationAccuracyReduced`

Via info.plist:
`<key>NSLocationDefaultAccuracyReduced</key><true/>`

### How it works

- NOT just adding random noise
- Snaps to a region describing "where I am" (think city-level)
- Region can be up to 10km

### Permission Request Changes

Added ability to skip provisional "always" state

How:
- First request only `.authorizedWhenInUse`
- Then request only `authorizedAlways` when needed

### CLActivityType

| CLActivityType | Use Case |
|-|-|
| airborne | flying or taxiing on runway |
| fitness | workout sessions (not normal nav) |
| automotiveNavigation | stays on roads (cars and road cycling) |
| otherNavigation | transport that may not stay on roads |
| other | none of the above |

## App Clips & Widgets

### App Clip

- App Clips can't get "Always"
- "When using" is only granted until next morning


### Widget

- `NSWidgetWantsLocation` in info.plist
- can't show prompts
- Inherits auth status from parent app