# Slides

Slides are plain Svelte components.

## Registration

Slides are added in `src/App.svelte` by importing components and placing them in the `slides` array.

```svelte
const slides = [IntroSlide, ChessboardSlide, CodeBlockSlide]
```

## Rendering

`Slides.svelte` renders one slide at a time and swaps components with the browser View Transitions API.

## Slide props

Slides can receive these props:

- `currentStep` - the active step index within the slide
- `onSlideMount(totalSteps)` - tells the shell how many steps this slide has

## Recommended pattern

```svelte
<script lang="ts">
  type Props = {
    currentStep?: number
    onSlideMount?: (totalSteps: number) => void
  }

  let { currentStep = 0, onSlideMount }: Props = $props()
  onSlideMount?.(3)
</script>

{#if currentStep === 0}
  <section>step one</section>
{:else if currentStep === 1}
  <section>step two</section>
{:else}
  <section>step three</section>
{/if}
```

## Notes

- Slides without steps should still call nothing; they behave like a single slide.
- Each step can use completely different markup and styling.
