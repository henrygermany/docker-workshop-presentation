<script lang="ts">
    import {getAllIcons} from "material-file-icons";

    export let lineNumbers: boolean | string | null = null;
    export let startFrom: string | null = null;
    export let id: string | null = null;
    export let description: string | null = null;

    export let language: string | null = null;

    export let iconType: string | null = null;


    const icon = iconType ? (getAllIcons().find(icon => icon.name === iconType)) : null;


</script>

<style>
    pre {
        margin-top: 0;
    }
</style>

<div class="flex flex-col items-center">

    {#if description !== null || iconType !== null}

        <div class="p-2 w-[90%] inline-flex my-0 items-center gap-1 justify-center text-sm border border-[#292C33]"
             data-id="{id}_header">
            {#if iconType !== null}
                    <span class="block w-[20px]">
                        {@html icon?.svg}
                    </span>
            {/if}
            {description ?? ''}
        </div>
    {/if}
    <pre class="{language}" data-id={id}>
    <code
            class="{`${description} ${$$props.class}`}"
            data-line-numbers={lineNumbers}
            data-ln-start-from={startFrom}
            data-noescape
            data-trim
            style="{`${$$props.style}`}"
    >
      <slot/>
    </code>
  </pre>
</div>


