# Examples

## Chessboard progression

Use steps to evolve one visual into another:

```svelte
{#if currentStep === 0}
  <Flip id="board"><Chessboard mode="pieces" /></Flip>
{:else}
  <Flip id="board"><Chessboard mode="bitboard" /></Flip>
{/if}
```

## Code highlighting

Show the same code block with different emphasis:

```svelte
{#if currentStep === 0}
  <Flip id="snippet"><CodeBlock highlightLines={[1, 2]} /></Flip>
{:else if currentStep === 1}
  <Flip id="snippet"><CodeBlock highlightLines={[5, 6]} /></Flip>
{:else}
  <Flip id="snippet"><CodeBlock highlightLines={[10]} /></Flip>
{/if}
```

## Totally different steps

Steps do not need to look related:

```svelte
{#if currentStep === 0}
  <section class="bg-black text-white">brutal</section>
{:else}
  <section class="bg-white text-black">minimal</section>
{/if}
```

## Suggested pattern

1. Pick a total step count
2. Call `onSlideMount(totalSteps)`
3. Branch on `currentStep`
4. Reuse `Flip` IDs for anything that should morph
