<script lang="ts">
  import Slides from './lib/components/Slides.svelte'
  import ChessboardSlide from './lib/slides/ChessboardSlide.svelte'
  import CodeBlockSlide from './lib/slides/CodeBlockSlide.svelte'
  import FlipShowcaseA from './lib/slides/FlipShowcaseA.svelte'
  import FlipShowcaseB from './lib/slides/FlipShowcaseB.svelte'
    import FlipShowcaseC from './lib/slides/FlipShowcaseC.svelte';
  import IntroSlide from './lib/slides/IntroSlide.svelte'

  const slides = [IntroSlide, ChessboardSlide, CodeBlockSlide, FlipShowcaseA, FlipShowcaseB, FlipShowcaseC]
</script>

<svelte:head>
  <title>Pierce v2</title>
  <meta
    name="description"
    content="A lean Svelte presentation system with view transitions, a chessboard component, and a clean code block."
  />
</svelte:head>

<Slides {slides} />
