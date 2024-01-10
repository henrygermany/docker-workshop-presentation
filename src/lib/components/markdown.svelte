<script lang="ts">
  export let external: string | null = null;

</script>

{#if external }
  <section data-markdown={external}>

  </section>
{:else}
  <section data-markdown>
    <div data-template>
      <slot />
    </div>
  </section>
{/if}