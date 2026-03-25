<script lang="ts">
  import Chessboard from '../components/Chessboard.svelte'
  import Flip from '../components/Flip.svelte'

  const piecesFen = 'r1bqkbnr/pppp1ppp/2n5/4p3/2B1P3/5N2/PPPP1PPP/RNBQ1RK1 b kq - 4 4'
  const bitboardFen = 'r1bqkbnr/pppp1ppp/2n5/4p3/2B1P3/5N2/PPPP1PPP/RNBQ1RK1 b kq - 4 4'
</script>

<section class="grid min-h-[calc(100dvh-4.5rem)] grid-cols-12 gap-5 px-3 py-2 md:px-4 md:py-4">
  <div class="col-span-12 md:col-span-4 md:py-8 lg:col-span-3">
    <p class="font-mono text-[10px] uppercase tracking-[0.32em] text-muted">chessboard</p>

    <Flip id="deck-title" as="h2" class="mt-4 max-w-[6ch] font-display text-[clamp(3rem,7vw,5.8rem)] leading-[0.9] tracking-[-0.05em]">
      chess.
    </Flip>

    <p class="mt-4 max-w-sm text-[15px] leading-7 text-ink/70">
      FEN in, board out. Pieces mode for visual boards, bitboard mode for cleaner binary layouts.
    </p>

    <ul class="mt-8 space-y-2 border-t border-line pt-4 font-mono text-[11px] uppercase tracking-[0.2em] text-muted">
      <li>fen parsing</li>
      <li>pieces mode</li>
      <li>bitboard mode</li>
    </ul>
  </div>

  <div class="col-span-12 grid gap-5 md:col-span-8 lg:col-span-9 xl:grid-cols-2">
    <Flip id="board-demo" class="block">
      <Chessboard
        fen={piecesFen}
        mode="pieces"
        title="opening shape"
        subtitle="high-contrast pieces / glass shell"
        class="w-full"
      />
    </Flip>

    <Flip id="board-demo-2" class="block">
      <Chessboard
        fen={bitboardFen}
        mode="bitboard"
        title="bitboard view"
        subtitle="same component / lean data mode"
        class="w-full"
      />
    </Flip>
  </div>
</section>
