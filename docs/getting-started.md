# Getting Started

## Install

```bash
bun install
```

## Run locally

```bash
bun dev
```

Open the app at `http://localhost:5173`.

## Build

```bash
bun run build
```

## Check types

```bash
bun run check
```

## Controls

- `ArrowRight` / `Space` / `PageDown` - next step or next slide
- `ArrowLeft` / `PageUp` - previous step or previous slide

## Project shape

- `src/App.svelte` defines the slide order
- `src/lib/components/Slides.svelte` handles navigation and transitions
- `src/lib/components/Flip.svelte` enables shared element animations
- `src/lib/components/Step.svelte` is a lightweight step wrapper
