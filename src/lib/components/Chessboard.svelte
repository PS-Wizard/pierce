<script lang="ts">
    import type { ClassValue } from "svelte/elements";

    type Mode = "pieces" | "bitboard";

    type Props = {
        fen?: string;
        title?: string;
        subtitle?: string;
        mode?: Mode;
        class?: ClassValue;
    };

    type Occupant = "white" | "black" | null;

    let {
        fen = "rnbqkbnr/pppppppp/8/8/8/8/PPPPPPPP/RNBQKBNR w KQkq - 0 1",
        title,
        subtitle,
        mode = "pieces",
        class: className,
    }: Props = $props();

    function parseFenToBoard(input: string) {
        const board: Occupant[] = [];
        const placement = input.split(" ")[0] ?? "";

        for (const row of placement.split("/")) {
            for (const token of row) {
                const empty = Number(token);

                if (!Number.isNaN(empty)) {
                    board.push(...Array.from({ length: empty }, () => null));
                    continue;
                }

                board.push(token === token.toUpperCase() ? "white" : "black");
            }
        }

        while (board.length < 64) board.push(null);

        return board.slice(0, 64);
    }

    const board = $derived(parseFenToBoard(fen));
    const cells = Array.from({ length: 64 }, (_, index) => index);
</script>

<figure
    class={[
        "w-full rounded-[2rem] border border-line bg-white/60 p-4 shadow-[0_24px_90px_rgba(0,0,0,0.08)] backdrop-blur-sm",
        className,
    ]}
    aria-label={title
        ? `${title}${subtitle ? ` — ${subtitle}` : ""}`
        : "Chessboard"}
>
    {#if title || subtitle}
        <figcaption
            class="mb-4 flex items-end justify-between gap-4 border-b border-line pb-3"
        >
            <div class="min-w-0">
                {#if title}
                    <p
                        class="font-display text-[1rem] uppercase tracking-[0.14em] text-ink"
                    >
                        {title}
                    </p>
                {/if}

                {#if subtitle}
                    <p
                        class="mt-1 font-mono text-[10px] uppercase tracking-[0.22em] text-muted"
                    >
                        {subtitle}
                    </p>
                {/if}
            </div>

            <p
                class="font-mono text-[10px] uppercase tracking-[0.22em] text-muted"
            >
                {mode}
            </p>
        </figcaption>
    {/if}

    <div
        class="grid aspect-square grid-cols-8 overflow-hidden rounded-[1.5rem] border border-line bg-paper"
    >
        {#each cells as cellIndex (cellIndex)}
            {@const row = Math.floor(cellIndex / 8)}
            {@const col = cellIndex % 8}
            {@const isDark = (row + col) % 2 === 1}
            {@const occupant = board[cellIndex]}

            <div
                class={[
                    "relative grid place-items-center",
                    isDark ? "bg-[#908a7f]" : "bg-[#f4efe5]",
                ]}
            >
                {#if mode === "pieces" && occupant}
                    <div
                        class={[
                            "h-[64%] w-[64%] rounded-full border border-black/10 shadow-[0_7px_18px_rgba(0,0,0,0.15)]",
                            occupant === "white"
                                ? "bg-[linear-gradient(145deg,#ffffff_0%,#eee8de_52%,#d9d1c4_100%)]"
                                : "bg-[linear-gradient(145deg,#41403d_0%,#141312_55%,#050505_100%)]",
                        ]}
                    ></div>
                {/if}

                {#if mode === "bitboard" && occupant}
                    <span class={"font-mono text-lg font-semibold"}> 1 </span>
                {/if}
            </div>
        {/each}
    </div>
</figure>
