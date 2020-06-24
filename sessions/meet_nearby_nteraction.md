# Meet Nearby Interaction

- Used by iOS 13 share sheet
- Requires U1 chip

Users opt in to session via permission dialog

Sessions are 1:1, but a device can be participating in multiple sessions

Updates are bidirectional and simultaneous

Starting a session:
`let session = NISession(configuration: NINearbyPeerConfiguration)`

NIDiscoveryToken
- temp
- randomly generated
- only valid for lifetime of the session

Each session has a discovery token
Need to share with other participant (multipeer framework or something else)

Steps to start a session:
- Create session for each peer
- Exchange tokens
- Createa session config with peer's token
- Run a session with a configuration
- Listen to delegate for session updates.

Delegate updates for:
- distance/direction updates
- peer lost/ended
- session lifecycle

Updates includes
- discoveryToken
- distance - optional
- direction - optional simd_float3 (3d unit vector)


Best Practices
- verify hardware support
- field of view matters (similar to wide angle lens on camera)
- orientation matters
- occulusions can break things

Simulator can be used for testing!