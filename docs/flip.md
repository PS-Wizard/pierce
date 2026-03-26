# Flip

`Flip` is the shared-element wrapper used for view transitions.

## What it does

It assigns a `view-transition-name` to the wrapped element, so matching IDs animate between renders.

## Basic usage

```svelte
<Flip id="hero-title" as="h1">Pierce v2</Flip>
```

## Matching rule

- Same `id` on two renders = animate between them
- Works across slides
- Works across steps
- Works for elements and components

## Example

```svelte
{#if currentStep === 0}
  <Flip id="board"><Chessboard mode="pieces" /></Flip>
{:else}
  <Flip id="board"><Chessboard mode="bitboard" /></Flip>
{/if}
```

## Tips

- Keep IDs stable for things you want to morph
- Wrap the smallest useful element
- You can use multiple Flip elements on the same slide
