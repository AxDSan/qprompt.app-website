# WebAssembly (WASM) Integration

One of the core features of the QPrompt website is the integration of the native teleprompter logic directly into the browser using WebAssembly.

## Assets

- `public/qprompt.wasm`: The compiled binary of the QPrompt application.
- `public/js/qtloader.js`: The loader script that handles fetching and instantiating the WASM module.
- `public/js/qprompt.js`: Integration logic that bridges the web environment with the WASM module.

## Critical Security Headers

For the WASM module to function correctly, especially if it uses multi-threading or shared memory, the browser requires the page to be "cross-origin isolated". This is achieved by serving the following headers:

```http
Cross-Origin-Opener-Policy: same-origin
Cross-Origin-Embedder-Policy: require-corp (or credentialless)
```

In this project, these headers are handled by:
1. `vite.config.js`: For the development server.
2. `main.js`: For the custom production/testing server.

## Initialization Flow

1. **Page Load:** The `init()` function in `index.html` is called on body load.
2. **Video Playback:** The hero section plays a promotional video (`website-prompter.webm`).
3. **WASM Loading:** `loadWasm()` is called immediately to start downloading the module in the background.
4. **Transition:** Once the video ends, a "TV turn-on" effect is triggered, and the WASM container (`#qt-shadow-container`) is revealed.
5. **WASM Entry:** The `qtLoad` function from `qtloader.js` initializes the module and attaches it to the `#screen` element.

## Performance Considerations

- The WASM module is large and is loaded asynchronously to avoid blocking the initial page render.
- The intro video serves as a visual bridge while the WASM module is being prepared in the background.

