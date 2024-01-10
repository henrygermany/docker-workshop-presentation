<script lang="ts">
  export let size: string = "text-9xl";
</script>

<div class="h-full w-full {size} flex justify-center">
  <slot />
</div>