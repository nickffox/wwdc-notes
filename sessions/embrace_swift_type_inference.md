# Embrace Swift Type Inference

Type Inference (TI) is ommitting type info where the compiler can figure it out

Types used in generics are called "Concrete Types"

## How Type Inference Works in the Compiler

TI algo fills in "pieces of the puzzle" 
Filling in one piece can unlock any other clues

TI algo integrates error-tracking
- records info about errors in source code
- attempts to fix to continue type inference

Swift 5.3 uses this new strategy for _all_ errors


## Fixing Compiler Errors

Compiler notes are "breadcrumbs" through your code for help debugging.

See: 
swift.org/blog/new-diagnostic-arch-overview/