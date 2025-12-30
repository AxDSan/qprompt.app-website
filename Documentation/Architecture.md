# Architecture Overview

This project is the official website for **QPrompt**, a professional-grade teleprompter application. The website is designed to be high-performance, visually engaging, and serves as a landing page for downloads, community engagement, and a live demo of the prompter.

## Technology Stack

- **Runtime:** [Bun](https://bun.sh/) (Preferred for development and devops)
- **Frontend Framework:** Vanilla HTML/JS with [Alpine.js](https://alpinejs.dev/) for reactive components.
- **Styling:** [Tailwind CSS](https://tailwindcss.com/) for modern, utility-first styling.
- **Build Tool:** [Vite](https://vitejs.dev/) for fast development and optimized production builds.
- **WASM Integration:** Uses WebAssembly to run the QPrompt core logic directly in the browser.
- **Animations:** [Motion One](https://motion.dev/) for smooth, high-performance web animations.

## Project Structure

- `index.html`: Main entry point (Vite).
- `main.js`: Custom CommonJS static server for production/testing with specific security headers required for WASM.
- `public/`: Static assets including:
  - `qprompt.wasm`: The core teleprompter logic compiled to WebAssembly.
  - `js/`: Scripts for WASM loading (`qtloader.js`) and application logic (`qprompt.js`).
  - `video/`: Promotional video used in the hero section.
  - `components/`: HTML fragments for modularity (e.g., navbar, footer).
- `src/`: Source files for Tailwind CSS processing.

## Key Features

1. **Live WASM Demo:** A functional version of QPrompt runs in the hero section after the intro video completes.
2. **Dynamic Downloads:** A filtered download section powered by Alpine.js for different versions and platforms.
3. **Responsive Design:** Fully responsive layout optimized for mobile and desktop.
4. **Security Headers:** Implements COOP (Cross-Origin-Opener-Policy) and COEP (Cross-Origin-Embedder-Policy) headers essential for shared memory in WASM.

## Component Integration

The website uses a hybrid approach:
- **Vite** handles the modern build pipeline and Tailwind JIT.
- **Custom Server (`main.js`)** provides a lightweight way to serve the site with the specific headers required by the WASM module without complex infrastructure.

