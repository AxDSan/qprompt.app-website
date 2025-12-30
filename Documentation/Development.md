# Development Guide

This guide provides information for developers looking to modify or contribute to the QPrompt website.

## Coding Standards

- **HTML:** Keep semantic and clean. Use Alpine.js for simple interactivity.
- **CSS:** Use Tailwind CSS utility classes. Avoid custom CSS unless absolutely necessary (stored in `src/input.css` or inline `<style>` tags for component-specific logic).
- **JavaScript:** Prefer modern ES6+ syntax. Keep the logic modular.
- **WASM:** The `qprompt.wasm` file is a compiled binary. Changes to the core prompter logic must be made in the main QPrompt repository and recompiled.

## Modifying the UI

Most of the UI components are defined directly in `index.html`. 

### Tailwind CSS
If you add new Tailwind classes, make sure the development server is running (`bun run dev`) so the JIT compiler can generate the necessary CSS.

### Alpine.js Components
Interactive parts like the download filters and the hero prompter logic are handled by Alpine.js. 
- Hero prompter logic: `heroPrompter` component defined in the script section of `index.html`.
- Download filters: Inline `x-data` in the `#downloads` section.

## Adding New Downloads

To add a new version or platform to the download section:
1. Locate the `#downloads` section in `index.html`.
2. Update the `ver` or `platform` buttons if needed.
3. Add the corresponding download cards using `x-show` to filter by version and platform.

## Deployment

The website is designed to be served as a static site. However, ensure the hosting environment supports the required COOP/COEP headers for WASM functionality.

