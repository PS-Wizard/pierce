# Steps

Steps let one slide behave like a sequence of mini-scenes.

## What steps do

- Keep one slide in the deck
- Advance one scene at a time inside that slide
- Reuse the same view transition system as normal slide changes

## How to define them

Inside a slide component:

```svelte
<script lang="ts">
  type Props = {
    currentStep?: number
    onSlideMount?: (totalSteps: number) => void
  }

  let { currentStep = 0, onSlideMount }: Props = $props()
  onSlideMount?.(2)
</script>

{#if currentStep === 0}
  <section class="bg-black text-white">first step</section>
{:else}
  <section class="bg-white text-black">second step</section>
{/if}
```

## Behavior

- Right arrow moves to the next step first
- When the last step is reached, the next press moves to the next slide
- Left arrow walks back through steps before moving to the previous slide

## Freedom

Each step can be visually unrelated to the last:

- different layout
- different background
- different spacing
- different component composition

## Step wrapper

`Step.svelte` exists as a lightweight semantic wrapper. Use it if you want to group step content clearly, but the navigation logic is driven by `currentStep` and `onSlideMount`.
