# study-shell

`study-shell` is an attempt to provide a common interface to the various
elements of different platform application frameworks. It is designed to be used
by [study], a UI toolkit.

## Design

The code in `study-shell` can be divided into roughly two categories: the
platform agnostic code and types, which are exposed directly, and the
platform-specific implementations of these types, which live in per-backend
directories in `src/backend`. The backend-specific code for the current
backend is reexported as `study-shell::backend`.

`study-shell` does not generally expose backend types directly. Instead, we
expose wrapper structs that define the common interface, and then call
corresponding methods on the concrete type for the current backend.

## Unsafe

Interacting with system APIs is inherently unsafe. One of the goals of
`study-shell` is to handle all interaction with these APIs, exposing
a safe interface to `study` and other possible consumers.

[study]: https://github.com/linebender/study
