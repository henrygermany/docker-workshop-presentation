<script lang="ts">
  export let lineNumbers: boolean | string | null = null;
  export let startFrom: string | null = null;
  export let id: string | null = null;
</script>


<pre
  data-id={id}
>
    <code
      data-trim
      data-noescape
      data-line-numbers={lineNumbers}
      data-ln-start-from={startFrom}
    >
      <slot />
    </code>
  </pre>
