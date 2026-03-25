<script lang="ts">
  import type { ClassValue } from 'svelte/elements'
  import type { Snippet } from 'svelte'

  type Props = {
    id: string
    as?: keyof HTMLElementTagNameMap
    class?: ClassValue
    style?: string
    children?: Snippet
  }

  let { id, as = 'div', class: className, style, children, ...rest }: Props = $props()
</script>

<svelte:element
  this={as}
  {...rest}
  class={['flip-root', className]}
  style={`${style ? `${style}; ` : ''}view-transition-name:${id};`}
  data-flip={id}
>
  {#if children}
    {@render children()}
  {/if}
</svelte:element>
