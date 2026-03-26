# Pierce

A clean, lean, high-performance presentation system built with Svelte 5, native View Transitions, and Tailwind CSS v4.

## Features

- **Native View Transitions** - Smooth, animations between slides and steps
- **Steps Within Slides** - Break complex slides into multiple steps with seamless transitions
- **Flip Component** - Match elements by ID across slides/steps for magical morphing animations
- **Keyboard Navigation** - Arrow keys and space for intuitive control
- **Component-Based Architecture** - Slides are just Svelte components
- **Zero Dependencies** - Uses browser-native APIs, no animation libraries

## Stack

- Svelte 5 + Vite
- Bun
- Tailwind CSS v4
- Native View Transitions API

## Components

- `Slides` - Core presentation engine with keyboard navigation
- `Flip` - Element wrapper for shared transitions across slides/steps
- `Step` - Semantic wrapper for multi-step slides
- `Chessboard` - FEN-based chess visualization (pieces/bitboard modes)
- `CodeBlock` - Syntax-highlighted code display

## Quick Start

```bash
bun install
bun dev
```

Visit `http://localhost:5173` and use arrow keys to navigate.

## Documentation

Comprehensive documentation is available in the `/docs` folder:

- [Getting Started](docs/getting-started.md) - Installation and basic setup
- [Creating Slides](docs/slides.md) - How to build and structure slides
- [Steps Guide](docs/steps.md) - Adding multi-step slides
- [Flip Component](docs/flip.md) - Shared element transitions
- [Examples](docs/examples.md) - Real-world patterns and techniques

## License

MIT
