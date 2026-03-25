<script lang="ts">
  import type { ClassValue } from 'svelte/elements'

  type Props = {
    code: string
    title?: string
    language?: string
    highlightLines?: number[]
    class?: ClassValue
  }

  let {
    code,
    title = 'snippet',
    language = 'text',
    highlightLines = [],
    class: className,
  }: Props = $props()

  let copied = $state(false)

  const lines = $derived(code.replace(/\n$/, '').split('\n'))
  const highlights = $derived(new Set(highlightLines))

  async function copyCode() {
    await navigator.clipboard.writeText(code)
    copied = true
    window.setTimeout(() => {
      copied = false
    }, 900)
  }
</script>

<section
  class={['selection-invert overflow-hidden border border-line bg-ink text-paper shadow-[0_24px_90px_rgba(0,0,0,0.12)]', className]}
>
  <header class="flex items-center justify-between gap-4 border-b border-white/10 px-4 py-3 md:px-5">
    <div class="min-w-0">
      <p class="font-mono text-[10px] uppercase tracking-[0.26em] text-paper/55">{language}</p>
      <h3 class="mt-1 truncate font-display text-[12px] uppercase tracking-[0.18em] text-paper">{title}</h3>
    </div>

    <button
      type="button"
      onclick={copyCode}
      class="shrink-0 border border-white/10 px-3 py-1.5 font-mono text-[10px] uppercase tracking-[0.22em] text-paper/70 transition hover:border-white/20 hover:text-paper"
    >
      {copied ? 'copied' : 'copy'}
    </button>
  </header>

  <div class="max-h-[70vh] overflow-auto px-4 py-4 font-mono text-[13px] leading-6 text-paper/90 md:px-5">
    {#each lines as line, index (index)}
      {@const lineNumber = index + 1}
      <div
        class={[
          'grid grid-cols-[3rem_minmax(0,1fr)] gap-4 px-3 py-1.5 transition',
          highlights.size > 0 && !highlights.has(lineNumber) ? 'text-paper/34' : 'text-paper/90',
          highlights.has(lineNumber) ? 'bg-white/10' : '',
        ]}
      >
        <span class="text-right tabular-nums text-paper/40">{lineNumber}</span>
        <span class="min-w-0 whitespace-pre-wrap break-words">{line || ' '}</span>
      </div>
    {/each}
  </div>
</section>
