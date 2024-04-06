<script>
    import { onMount } from "svelte";

    let intersecting = false;
    let intersected_count = 0;
    let container;
    let observer;
    let options = {
            root: null,
            rootmargin: "0px",
            threshold: 0
        }
    
    let callback = () => {
        if (intersected_count > 0) {
            intersecting = true;
            observer.unobserve(container);
        }
        intersected_count++;
    }

    onMount(() => {
        observer = new IntersectionObserver(callback, options);
        observer.observe(container);
    });

</script>

<div bind:this={container}>
    <slot {intersecting} ></slot>
</div>

<style>
    div {
        margin: 15px 0;
        width: 100%;
        height: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
        min-height: 150px;
    }
</style>
