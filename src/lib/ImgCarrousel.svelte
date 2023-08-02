<script>
    import { fade } from 'svelte/transition';
    import { cubicOut } from 'svelte/easing';
	import { onMount } from 'svelte';
    
    export let contents;
    export let width = 250;

    let active = 1;
    let autoplay = true;

    onMount(() => {
        const id = setInterval(() => {
            if(autoplay) {
                (active > 1) ? (--active) : (active = contents.length);
            }
        }, 3000);

        return () => { clearInterval(id) };
    });
</script>

<div class="imgCarrousel">
    <button on:click={
        (e) => { 
            (active < contents.length) ? (++active) : (active = 1);
            autoplay = false;
            setTimeout(() => { autoplay = true }, 5000);
        }
    }>
        <img src="./images/arrow.svg" alt="Previous">
    </button>
    {#each contents as img}
        {#if img.id == active}
            <img
                src={img.src}
                alt={img.alt}
                style="width: {width}px;"
                in:fade={{ duration:1500, easing:cubicOut }}
            />
        {/if}
    {/each}
    <button on:click={
        (e) => { 
            (active > 1) ? (--active) : (active = contents.length);
            autoplay = false;
            setTimeout(() => { autoplay = true }, 10000);
        }
    }>
        <img src="./images/arrow.svg" alt="Next" style="rotate: 180deg;">
    </button>
</div>

<style>
    .imgCarrousel {
        display: flex;
        overflow-x: hidden;
        align-items: center;
        width: fit-content;
    }
    
    img {
        aspect-ratio: 288 / 250;
    }
    
    button {
        border-radius: 50%;
        width: 60px;
        aspect-ratio: 1 / 1;
        cursor: pointer;
        background-color: gray;
        opacity: 75%;
        margin: 10px;
        box-shadow: 2px 2px 0 lightgray;
    }
    
    button > img {
        width: 40px;
        aspect-ratio: 1 / 1;
        padding: 0;
        margin: 0;
    }
</style>