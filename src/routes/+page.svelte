<script>
    import { onMount } from "svelte";
    import LoadingIcon from "../lib/LoadingIcon.svelte";
    import ImageLoader from "../lib/ImageLoader.svelte";
    import { fade } from "svelte/transition";

    const sleep = ms => new Promise(r => setTimeout(r, ms));

    let loading = true;
    let loading_text = "Ucitavam";

    let loading_text_change = async () => {
        await sleep(1200);
        loading_text = "Ide pokloncic"
        await sleep(2000);
        loading_text = "Dodajem slike"
        await sleep(2000);
        loading_text = "Svrsavam"
        await sleep(300);
        loading_text = "Zavrsavam*"
        await sleep(1000);
        loading = false;
    }

    onMount(() => {
        loading_text_change();
    });
</script>

{#if loading}
    <div class="loading" transition:fade>
        <span>{loading_text}</span>
        <LoadingIcon color="white" />
    </div>
{/if}

<main>
    <h1 class="animated-text">Srecan 19. rodjendan brate 🎉🎉🥳</h1>
    <p class="subheader animated-text">To Sergej Sucur</p>

    <div class="gallery">
        <ImageLoader src="serz.jpg" alt="img" fireNow/>
        <ImageLoader src="us.jpg" alt="img" fireNow/>
        <ImageLoader src="gmod.jpg" alt="img" />
        <ImageLoader src="litica.jpg" alt="img" />
        <ImageLoader src="halflife.png" alt="img" />
        <ImageLoader src="log.png" alt="img" />
        <ImageLoader src="factorio.png" alt="img" />
        <ImageLoader src="factorio2.png" alt="img" />
        <ImageLoader src="wow.png" alt="img" />
    </div>

    <div class="wish">
        Zelim brate da te manje jebe zivot i naravno da manje mislis o tome i o sitnicama koje ce proci.
        Nadam se da cemo se druziti vise i da manje iko utice na nase drustvo.
        Zeli grisha, srecan rodjendan.
    </div>
</main>

<style>
    :root {
        color: black;
        font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
    }
    h1 {
        text-align: center;
        font-size: 2.5rem;
        margin-top: 50px;
    }
    .subheader {
        text-align: center;
    }
    .gallery {
        margin-top: 50px;
        display: flex;
        justify-content: center;
        align-items: center;
        flex-direction: column;
    }
    .wish {
        text-align: center;
        margin-top: 150px;
    }
    .animated-text {
        background: linear-gradient(
            to right,
            #7953cd 20%,
            #00affa 30%,
            #0190cd 70%,
            #764ada 80%
        );
        -webkit-background-clip: text;
        background-clip: text;
        -webkit-text-fill-color: transparent;
        /* text-fill-color: transparent; */
        background-repeat: repeat;
        background-size: 400% auto;
        animation: textShine 2.8s ease-in-out infinite;
    }
    * {
        margin: 0;
        padding: 0;
    }
    .loading {
        top: 0;
        left: 0;
        position: fixed;
        color: white;
        background-color: black;
        width: 100%;
        height: 100%;
        display: flex;
        justify-content: center;
        align-items: center;
        font-weight: bold;
        z-index: 500;
        font-size: 2rem;
        overflow: hidden;
    }
    .loading * {
        margin: 5px;
    }
    @keyframes textShine {
        0% {
            background-position: 0% 50%;
        }
        100% {
            background-position: 100% 50%;
        }
    }
</style>