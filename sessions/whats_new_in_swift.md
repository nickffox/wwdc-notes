# What's New in Swift

## Performance

#### Binary Size

compared to objective-c
- 1.5x
SwiftUI
- 43% smaller than Xcode 11

Clean Memory
Dirty Memory - allocated and manipulated at runtime

Swift 5.3 head size < 1/3 of Swift 5.1

Swift moved below foundation in stack
- previously c had to be used

New diagnostic system
- better errors in SwiftUI

### Code Completion

impoved type-checking
15x faster (some cases) vs Xcode 11.5

### Code Indentation
Improved indentation for:
- Chained method calls
- Call args
- Tuple args
- Elements
- Collection eleements spanning multiple lines
- Multi-line control flow (if, guard, etc)

### Debugging

LLDB can now resolve objc-c types in swift using debug info
- better reliability (expression evaluator/variable view)

### Supported Platforms

- Apple Platform
- Ubuntu 16.04, 18.04, 20.04
- CentOS 8
- Amazon Linux 2
- Windows (coming soon in 5.3)


## Language and Libraries

### SE-0281  - Multiple Trailing Closure Syntax

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

### SE-0249 Keypaths as Functions

```swift
Struct Person {
    let name: String
}

let names = people.map(\.name) // \.name is (Person) -> String
```

### SE-0281 Type-Based Program Entry Point

Previously - @UIApplicationMain

New general form `@main`. Can be used with:
- ParsableCommand
- UIApplicationDelegate
- App
- etc

### SE-0269 - Increased availablity of implicit self in closures

- Omit self from struct/enum closures
- Include self in capture list, then don't need it in closure.

### SE-0276 - Multi-pattern Catch Clauses

ex:
```swift
do {
    // thing
} catch Error.noSuchFile, Error.notDirectory {
    // handle
} catch {
    // default handling
}
```

### SE-0266 - Synthesized comparable conformance for enums


### SE-0280 - Enum Cases as Protocol Witnesses

Enum cases can now be used to fulfill static protocol requirements

### SE-????

Switch is supported in in function builders

### SE-0277 - Float16

- IEEE 754 standard
- half width
- perf gainz

## Apple Archive

- modular archive formate
- multithreaded
- command line and finder integration

## Swift System
- idiomatic Swift interfaces to system calls
- low level currency types

## OSLog
- privacy sensitive logging
- string interpolation and formatting options
- faster

Explore Logging in Swift

## Packages

### Swift Numerics
- basic math functions for generic contexts
- complex numbers and arithmatic
- approximate equality

### Swift ArgumentParser

### Swift StandardLibraryPreview



