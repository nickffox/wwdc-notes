# Distribute Binary Frameworks as Swift Packages

Can now distribute xcpackage (binary) via SPM

Using binary via SPM is just like any other SPM package

## Distributing

New target type `binaryTarget`
- name
- url
- checksum


Only supported on apple platforms
Downloaded separately from open-source packages

## Creating

Get Checksum
`$ swift package compute-checksum zippedpackage.zip`

1. Select "Build libraries for Distribution"
2. Archive each variant
3. `$ xcodebuild -create-xcframework`


## Tradeoffs

Debugging is harder
Fixing isn't possible
Limited to archs that are distributed


