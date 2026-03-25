<script lang="ts">
    type SlideComponent = any;

    type Props = {
        slides?: SlideComponent[];
    };

    type NativeTransitionDocument = Document & {
        startViewTransition?: (
            updateCallback: () => void | Promise<void>,
        ) => { finished: Promise<void> };
    };

    let { slides = [] }: Props = $props();

    let current = $state(0);
    let busy = $state(false);

    const activeSlide = $derived(slides[current] ?? slides[0]);

    function clamp(index: number) {
        if (!slides.length) return 0;
        return Math.min(Math.max(index, 0), slides.length - 1);
    }

    function move(direction: -1 | 1) {
        if (!slides.length || busy) return;

        const nextIndex = clamp(current + direction);

        if (nextIndex === current) return;

        const update = () => {
            current = nextIndex;
        };

        const transitionDocument = document as NativeTransitionDocument;

        if (transitionDocument.startViewTransition) {
            busy = true;
            const transition = transitionDocument.startViewTransition(update);
            transition.finished.finally(() => {
                busy = false;
            });
            return;
        }

        update();
    }

    function onKeydown(event: KeyboardEvent) {
        const target = event.target as HTMLElement | null;
        const tagName = target?.tagName;

        if (
            tagName === "INPUT" ||
            tagName === "TEXTAREA" ||
            target?.isContentEditable
        ) {
            return;
        }

        if (
            event.key === "ArrowRight" ||
            event.key === " " ||
            event.key === "PageDown"
        ) {
            event.preventDefault();
            move(1);
        }

        if (event.key === "ArrowLeft" || event.key === "PageUp") {
            event.preventDefault();
            move(-1);
        }
    }
</script>

<svelte:window onkeydown={onKeydown} />

<main class="relative min-h-dvh overflow-hidden bg-paper text-ink">
    <div class="pointer-events-none absolute inset-0 opacity-[0.95]">
        <div class="absolute inset-x-0 top-0 h-px bg-line/80"></div>
        <div class="absolute inset-x-0 bottom-0 h-px bg-line/80"></div>
        <div
            class="absolute inset-y-0 left-[6%] hidden w-px bg-line/70 lg:block"
        ></div>
        <div
            class="absolute inset-y-0 left-1/2 hidden w-px -translate-x-1/2 bg-line/45 xl:block"
        ></div>
        <div
            class="absolute inset-0 bg-[radial-gradient(circle_at_top_right,rgba(255,255,255,0.75),transparent_34%),radial-gradient(circle_at_bottom_left,rgba(214,31,38,0.05),transparent_28%)]"
        ></div>
    </div>

    <section
        class="relative z-10 min-h-dvh px-2 pb-2 pt-2 md:px-6 md:pb-6 md:pt-6"
    >
        {#if activeSlide}
            {@const Current = activeSlide}
            <Current />
        {/if}
    </section>

    <div
        class="pointer-events-none absolute bottom-4 left-5 z-10 font-mono text-[10px] uppercase tracking-[0.25em] text-muted md:left-8"
    >
        arrow keys / space
    </div>
</main>
