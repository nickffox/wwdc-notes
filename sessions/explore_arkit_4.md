# Explore ARKit 4

## Location Anchor

Geo-ref AR content
- lat 
- lon
- alt

Apple maps visual localization

All on device

ARGeoTrackingConfiguration
- used to create/config session
- `.isSupported` - can device do this?
- `.checkAvailablility` - has permissions, and is supported at location?

ARGeoAnchor
- like other ar anchors
- use rendering engine to adjust/rotate anchors
  - fixed to cardinal directions
  - x axis always east
  - z axis always south

NOTE: Maps App can be helpful getting lat/lon

ARGeoTrackingStatus
- feedback on status
- state - how far along geolocation is
- state reason - why 
- accuracy - how good geolocation is
- monitor state transitions
  - Initializing -> Localizing -> Localized
  - Initializing -> Not Available

AGGeoTrackingStateReason
- why things are broken
  - devicePointedTooLow
  - dataNotAvailable

`ARSession.getGeoLocation` - get location anchor from scene (user tap)

Where Available:
- SFBayArea
- NY
- LA
- Chicago
- Miami
- More soon!

Limit access w/ required capability keys in info.plist
- gps
- iphon-ipad-minimum-performanc-a12

## Scene Geometry - LiDAR

Topological map of environment

Helpfule for 
- classification
- occlusion
- object detection
- lighting

## Depth API

NOTE: Requires `.supportsFrameSemantics(.sceneDepth)` (only LiDAR devices)

Data served at 60fps

measured in meters from the camera

`ARFrame.sceneDepth`
`ARDepthData`
- `depthMap` (CVPixelBuffer)
- `confidenceMap` (low, medium, or high)

## Object Placement

raycasting
- faster w/ LiDAR
- use raycasting over hittest in iOS14+

raycasting query
- target - the surface
- alignment - h, v, or any

## Face Tracking

- now A12+
- trueDepth camera adds capture depth data