# Explore Logging in Swift

New Swift logging APIs

Logs are:
- archived on device
- low perf overhead

## Creating Logs

```swift
import os

let logger = Logger(subsystem: "com.foo", category: "bar")
logger.log("This is my log")
logger.log("This is my log with data: \(someData)")
```

Pass data into logs using string interpolation - like print


`log` isn't like `print` though...
- logs aren't always converted to String (slow) - only when _displayed_
- format is based on the type of logged data

Data types supoorted in logs:
    - Numeric (Int/Double)
    - Objc-C (description)
    - CustomStringConvertible

Nonnumeric values are redacted by default
- default to protecting PII
- see [privacy section](#privacy) for more info

## Retrieving Logs

```sh
# fruta.logarchive is the "output" file name
$log collect --device --start '2020-06-22 0:41:00' --output fruta.logarchive
```

Open logs in Console.app

## Log Levels

### Debug
- only during debugging
- not persisted
- fastest - compiler optimizes away unless streaming logs

### Info
- helpful, but not required for troubleshooting
- persisted for a short time

### Notice (Default)
- required for troubleshooting
- persisted up to storage limit

### Error
- error during execution
- persisted up to storage limit

### Fault
- bug
- persisted up to storage limit
- slowest (but still fast)

## Formating Log Data

- Optional formatting parameters!
- Pass with data (like shown in [privacy section](#privacy) above).
- No additional runtime cost


## Privacy

Privacy modifiers can be applied to logged data:
- `.public` - shows info
- `.private(mask: .hash)`

Example of hiding PII in logs
```swift
logger.log("Ordered smoothie \(smoothieName, privacy: .public)")
```

## Version Support

- New APIs on new OS versions
- backward support for string interpolation via overloads