# XCTSkip Your Tests

Add runtime checks to enforce test requirements

Introduced in Xcode 11.4

Results:
- Pass
- Fail
- Skip

Ways to Skip

- throw `XCTSkip`
- `XCTSkipIf`
- `XCTSkipUnless`

```swift
guard #avilable(iOS 13.4, *) else {
    throw XCTSip("description")
}

try XCTSkipIf(UIDevice.current.userInterfaceIdiom != .pad, "message")
```

Skip is indicated:
- The test (at the point that triggered skip)
- Test Navigator
  - filter button
- Test Report