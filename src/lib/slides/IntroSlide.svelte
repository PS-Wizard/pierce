<script lang="ts">
  import Flip from '../components/Flip.svelte'
</script>

<section class="grid min-h-[calc(100dvh-4.5rem)] grid-cols-12 gap-5 px-3 py-2 md:px-4 md:py-4">
  <div class="col-span-12 flex flex-col justify-between gap-10 md:col-span-8 md:py-8 lg:col-span-7">
    <div class="max-w-3xl">
      <p class="font-mono text-[10px] uppercase tracking-[0.32em] text-muted">pierce-v2 / svelte / bun</p>

      <Flip id="deck-title" as="h1" class="mt-5 max-w-[8ch] font-display text-[clamp(4.5rem,11vw,10rem)] leading-[0.88] tracking-[-0.06em]">
        Pierce v2
      </Flip>

      <p class="mt-6 max-w-xl text-[clamp(1rem,1.8vw,1.4rem)] leading-8 text-ink/72 md:text-balance">
        Lean slides, native transitions, and a small component set that does a lot without a lot of CSS.
      </p>
    </div>

    <div class="grid gap-4 border-t border-line pt-4 text-[12px] leading-6 text-muted md:grid-cols-3">
      <div>
        <p class="font-mono text-[10px] uppercase tracking-[0.24em] text-ink">Slides</p>
        <p class="mt-2">Just components in an array.</p>
      </div>
      <div>
        <p class="font-mono text-[10px] uppercase tracking-[0.24em] text-ink">Flip</p>
        <p class="mt-2">Wrap any element or component with an id.</p>
      </div>
      <div>
        <p class="font-mono text-[10px] uppercase tracking-[0.24em] text-ink">CSS</p>
        <p class="mt-2">Tailwind first. Small globals. Calm surface.</p>
      </div>
    </div>
  </div>

  <div class="col-span-12 md:col-span-4 md:py-8 lg:col-span-5">
    <div class="grid gap-4">
      <div class="rounded-[2rem] border border-line bg-white/75 p-5">
        <p class="font-mono text-[10px] uppercase tracking-[0.24em] text-muted">controls</p>
        <p class="mt-3 text-[15px] leading-7 text-ink/70">Arrow keys / space to move.</p>
      </div>

      <div class="rounded-[2rem] border border-line bg-white/75 p-5">
        <p class="font-mono text-[10px] uppercase tracking-[0.24em] text-muted">selection</p>
        <p class="mt-3 text-[15px] leading-7 text-ink/70">No blue. Black selection on light surfaces, white selection on dark surfaces.</p>
      </div>
    </div>
  </div>
</section>
