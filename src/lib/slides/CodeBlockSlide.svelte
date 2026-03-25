<script lang="ts">
  import CodeBlock from '../components/CodeBlock.svelte'
  import Flip from '../components/Flip.svelte'

  const code = `<Flip id="board-demo">
  <Chessboard fen={fen} />
</Flip>

<CodeBlock
  title="slides.svelte"
  language="svelte"
  code={code}
  highlightLines={[1, 2, 4]}
/>
`
</script>

<section class="grid min-h-[calc(100dvh-4.5rem)] grid-cols-12 gap-5 px-3 py-2 md:px-4 md:py-4">
  <div class="col-span-12 md:col-span-4 md:py-8 lg:col-span-3">
    <p class="font-mono text-[10px] uppercase tracking-[0.32em] text-muted">codeblock</p>

    <Flip id="code-title" as="h2" class="mt-4 max-w-[6ch] font-display text-[clamp(3rem,7vw,5.8rem)] leading-[0.9] tracking-[-0.05em]">
      code.
    </Flip>

    <p class="mt-4 max-w-sm text-[15px] leading-7 text-ink/70">
      No syntax coloring. Better rhythm, spacing, and copy behavior for slide code.
    </p>
  </div>

  <div class="col-span-12 md:col-span-8 lg:col-span-9">
    <Flip id="snippet" class="block">
      <CodeBlock title="flip + board" language="svelte" code={code} highlightLines={[1, 2, 4]} class="w-full" />
    </Flip>
  </div>
</section>
