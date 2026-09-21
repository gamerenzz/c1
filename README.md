# CMG Backend Android

This is a GitHub-buildable Android project that packages the Windows CMG runtime assets (`cmg.slim.js`, `cmg.wasm`, `eb_prog.bin`, `reloc_table.bin`) and provides a GUI, foreground/background service, local HTTP HLS endpoint, and selectable/copyable logs.

## Build

Push the repository to GitHub. GitHub Actions -> `Android APK` -> artifact `cmg-backend-debug-apk`.

## Important status

The local HTTP server currently implements a transparent HLS proxy for an **authorized/user-supplied HLS/M3U8 URL**. The CMG runtime is loaded in a hidden WebView for runtime validation, but the final byte-for-byte CMG decrypt path is deliberately not claimed as complete yet: the Windows package's live-session initialization metadata and the exact HLS/CMG adapter need a real authorized playback fixture before the local endpoint can truthfully be advertised as fully decoded audio/video.

Therefore this ZIP is an Android engineering base, not a claim that protected live channels already play end-to-end. Do not use it to bypass authorization or access controls.
