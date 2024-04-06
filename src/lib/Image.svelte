<script>
    export let src;
    export let alt;

    import { onMount } from "svelte";
    import LoadingIcon from "./LoadingIcon.svelte";

    let loaded = false;
    let thisImage;

    onMount(() => {
        thisImage.onload = () => {
            loaded = true;
        };
        if (thisImage.complete) {
            loaded = true;
        }
    });

    
</script>

{#if !loaded}
    <LoadingIcon color="black" />
{/if}

<img {src} {alt} class:loaded bind:this={thisImage} />

<style>
    img {
        width: 0;
        height: 400px;
        opacity: 0;
        border-radius: 5px;
        transition: opacity 1200ms ease-out;
    }
    .loaded {
        width: 90% !important;
        height: auto !important;
        opacity: 1;
    }
</style>
