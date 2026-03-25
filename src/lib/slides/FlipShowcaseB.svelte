<script lang="ts">
    import Flip from "../components/Flip.svelte";
</script>

<section
    class="grid min-h-[calc(100dvh-4.5rem)] grid-cols-12 gap-5 px-3 py-2 md:px-4 md:py-4"
>
    <div class="col-span-12 md:col-span-4 md:py-8 lg:col-span-3">
        <p class="font-mono text-[10px] uppercase tracking-[0.32em] text-muted">
            flip
        </p>
        <h2
            class="mt-4 max-w-[7ch] font-display text-[clamp(3rem,7vw,5.8rem)] leading-[0.9] tracking-[-0.05em]"
        >
            rearranged.
        </h2>
        <p class="mt-4 max-w-sm text-[15px] leading-7 text-ink/70">
            Same ids, different layout. The browser handles the interpolation.
        </p>
    </div>

    <div
        class="col-span-12 grid gap-4 md:col-span-8 md:grid-cols-3 xl:grid-cols-3"
    >
        <Flip
            id="beta-card"
            class="selection-invert rounded-[1.5rem] border border-line bg-ink p-5 text-paper"
        >
            <p
                class="font-mono text-[10px] uppercase tracking-[0.28em] text-paper/55"
            >
                beta
            </p>
            <p class="mt-6 text-[1.5rem] leading-tight tracking-[-0.04em]">
                Each matching element moves in parallel.
            </p>
        </Flip>

        <Flip
            id="gamma-card"
            class="selection-invert rounded-[1.5rem] border border-line bg-ink p-5 text-paper"
        >
            <p
                class="font-mono text-[10px] uppercase tracking-[0.28em] text-paper/55"
            >
                gamma
            </p>
            <p class="mt-6 text-[1.5rem] leading-tight tracking-[-0.04em]">
                Unmatched space simply fades between states.
            </p>
        </Flip>

        <Flip
            id="alpha-card"
            class="selection-invert rounded-[1.5rem] border border-line bg-ink p-5 text-paper"
        >
            <p
                class="font-mono text-[10px] uppercase tracking-[0.28em] text-paper/55"
            >
                alpha
            </p>
            <p class="mt-6 text-[1.5rem] leading-tight tracking-[-0.04em]">
                Tall card with more copy and a darker surface.
            </p>
        </Flip>
    </div>
</section>
