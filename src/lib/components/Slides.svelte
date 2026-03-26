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
    let currentStep = $state(0);
    let busy = $state(false);

    const activeSlide = $derived(slides[current] ?? slides[0]);

    // Track total steps for current slide
    let currentSlideTotalSteps = $state(1);

    function onSlideMount(totalSteps: number = 1) {
        currentSlideTotalSteps = totalSteps;
    }

    function clamp(index: number) {
        if (!slides.length) return 0;
        return Math.min(Math.max(index, 0), slides.length - 1);
    }

    function move(direction: -1 | 1) {
        if (!slides.length || busy) return;

        if (direction === 1) {
            // Moving forward
            if (currentStep < currentSlideTotalSteps - 1) {
                // More steps in current slide
                transitionUpdate(() => {
                    currentStep += 1;
                });
            } else {
                // Move to next slide
                const nextIndex = clamp(current + 1);
                if (nextIndex !== current) {
                    transitionUpdate(() => {
                        current = nextIndex;
                        currentStep = 0;
                        currentSlideTotalSteps = 1; // Reset for next slide
                    });
                }
            }
        } else {
            // Moving backward
            if (currentStep > 0) {
                // Go to previous step
                transitionUpdate(() => {
                    currentStep -= 1;
                });
            } else {
                // Move to previous slide
                const prevIndex = clamp(current - 1);
                if (prevIndex !== current) {
                    transitionUpdate(() => {
                        current = prevIndex;
                        currentStep = 0;
                        currentSlideTotalSteps = 1; // Reset for previous slide
                    });
                }
            }
        }
    }

    function transitionUpdate(update: () => void) {
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

<section class="h-full">
    {#if activeSlide}
        {@const Current = activeSlide}
        <Current {currentStep} {onSlideMount} />
    {/if}
</section>
