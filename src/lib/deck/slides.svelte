<script lang="ts">
    import Reveal from "reveal.js";
    import Markdown from "reveal.js/plugin/markdown/markdown";
    import Highlight from "reveal.js/plugin/highlight/highlight";
    import Notes from "reveal.js/plugin/notes/notes";
    import {onMount} from "svelte";

    import "reveal.js/dist/reveal.css";
    import "reveal.js/dist/theme/black.css";
    import 'highlight.js/styles/atom-one-dark.css';

    import Presentation from "./presentation.svelte";

    onMount(() => {
        const deck = new Reveal();

        deck.initialize({
            plugins: [
                Markdown, Highlight, Notes
            ],
            autoAnimateEasing: "ease",
            controls: true,

            progress: true,
            slideNumber: true,
            showNotes: false,
            hash: true
        });
    });

</script>

<div class="reveal">
    <div class="slides">
        <Presentation/>
    </div>
</div>
