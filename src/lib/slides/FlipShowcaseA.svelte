<script lang="ts">
  import Flip from '../components/Flip.svelte'
</script>

<section class="grid min-h-[calc(100dvh-4.5rem)] grid-cols-12 gap-5 px-3 py-2 md:px-4 md:py-4">
  <div class="col-span-12 md:col-span-4 md:py-8 lg:col-span-3">
    <p class="font-mono text-[10px] uppercase tracking-[0.32em] text-muted">flip</p>
    <h2 class="mt-4 max-w-[7ch] font-display text-[clamp(3rem,7vw,5.8rem)] leading-[0.9] tracking-[-0.05em]">
      matching ids.
    </h2>
    <p class="mt-4 max-w-sm text-[15px] leading-7 text-ink/70">
      Multiple elements can animate together when the same ids exist on the next slide.
    </p>
  </div>

  <div class="col-span-12 grid gap-4 md:col-span-8 xl:grid-cols-3">
    <Flip id="alpha-card" class="rounded-[1.5rem] border border-line bg-white/75 p-5">
      <p class="font-mono text-[10px] uppercase tracking-[0.28em] text-muted">alpha</p>
      <p class="mt-8 text-[2rem] leading-none tracking-[-0.05em]">A</p>
    </Flip>

    <Flip id="beta-card" class="rounded-[1.5rem] border border-line bg-white/75 p-5">
      <p class="font-mono text-[10px] uppercase tracking-[0.28em] text-muted">beta</p>
      <p class="mt-8 text-[2rem] leading-none tracking-[-0.05em]">B</p>
    </Flip>

    <Flip id="gamma-card" class="rounded-[1.5rem] border border-line bg-white/75 p-5">
      <p class="font-mono text-[10px] uppercase tracking-[0.28em] text-muted">gamma</p>
      <p class="mt-8 text-[2rem] leading-none tracking-[-0.05em]">C</p>
    </Flip>
  </div>
</section>
