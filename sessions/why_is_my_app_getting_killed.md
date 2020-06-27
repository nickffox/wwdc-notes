# Why is My App Getting Killed

New MetricKit API

- `MXBackgroundExitData` 
  - gives counts of each termination type
  - includes user killing via app switcher

## Crashes

New `MXCrashDiagnostic`
- stack trace
- signal
- exception
- termination reason

## Watchdog
- timeout during transitions
- disabled in simulator and in debugger
- produces MXCrashDiagnostic

## CPU Resource Limit

`MXCPUExceptionDiagnostic`
- call stack can help find "hotspots"

## Memory Footprint

< 200mb for iPhone 6s

## Memory Pressure Exit (jetsam)

- Most common reason for being killed
- System freeing up memory
- Aim for < 50mb in BG
  - clear cache
  - clear images
  - flush state

## Background Task Timeout

These don't reproduce in the debugger
Count exposed via `MXBackgroundExitData`
No crash logs
Preventable!
- keeping bg task < 30 seconds
- use named variant of bgTask to help ID problematic tasks
- use expiration handler on all tasks

Debug using telemetry on start/end of expiration handlers

In `MXMetricsPayload` look at `signpostMetrics` property

You can leverage backgroundTimeRemaining