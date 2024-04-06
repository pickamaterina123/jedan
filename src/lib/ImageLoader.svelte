<script>
    export let src;
    export let alt;
    export let fireNow = false;

    import IntersectionObserver from "./Intersection.svelte";
    import Image from "./Image.svelte";
</script>

{#if fireNow}
    <div>
        <Image {alt} {src} />
    </div>
{:else}
    <IntersectionObserver let:intersecting>
        {#if intersecting}
            <Image {alt} {src} />
        {/if}
    </IntersectionObserver>
{/if}

<style>
    div {
        margin: 15px 0;
        width: 100%;
        height: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
        min-height: 400px;
    }
</style>
