# What's New in RealityKit

## Video Materials

- Can use videos as textures
- Video instructions
  - create a plane and map a video onto it
- Produce spatialized audio

How?
- Load video into AVPlayer
- Create VideoMaterial
- Apply to a model

Can interact with video using AVPlayer
- play pause
- notify on video state transitions
- loop
- serve remote media

## Scene Understanding (LiDAR)

GOAL - virtual content interact with real world

ARView -> Environment -> Scene Understanding

### occlusion
- `sceneUnderstanding.options.insert(.occlusion)`

### receives lighting (auto enabled occlusion)
- `sceneUnderstanding.options.insert(.receivesLighting)`
- shadows straight down by default

### physics (auto enables collision)
- `sceneUnderstanding.options.insert(.physics)`
- real world objects are static with infinite mass
- only visible (scanned) regions are included
- mesh is approximate
- no collaborative sessions

### collision
- `sceneUnderstanding.options.insert(.collision)`
- use for
  - raycasting
  - collision detection

New sceneUnderstanding entity 
- IMPORTANT: consider these read only
- represents real world object
- use `HasSceneUnderstanding` trait to identify

New SceneUnderstanding collision group
- use to filter out real world collisions

Debug real-world mesh
- `arView.debugOptins.insert(.showSceneUnderstanding)`
- NOTE: Only shows the real-world mesh

## Improved Rendering Debugging

DebugModelComponent(shaderDebugMode:)

NOTE: Only applied to targeted entity (NOT CHILDREN)

## Integration with ARKit 4

### Face Tracking

More devices (any A12+)

### Location Anchors

Anchors for real-world coordinates
SceneUnderstanding won't work b/c `ARGeoTrackingConfiguration` isn't a `WorldTrackingConfiguration`