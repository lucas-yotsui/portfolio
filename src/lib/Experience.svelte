<script>
	import { cubicInOut } from "svelte/easing";
	import { tweened } from "svelte/motion";
	import ImgCarrousel from "./ImgCarrousel.svelte";
    
    export let experience;
    export let expanded = null;
    
    let topicsSize = tweened(0, { duration: 800, easing: cubicInOut });
</script>

<div 
    role="region"
    class="experience"
    on:mouseenter={(e) => { topicsSize.set(1) }}
    on:mouseleave={(e) => { topicsSize.set(0) }}
>
    <h1>{ experience.title }</h1>

    <ImgCarrousel
        contents={ experience.imgs }
        width={ 200 }
    >
    </ImgCarrousel>

    <div 
        class="itemsExpanded"
        style="max-height: { $topicsSize * 800 }px; opacity: { $topicsSize }"
    >
        <ul>
            {#each experience.topics as topic}
                <li>{ topic }</li>
            {/each}
        </ul>    
        
        <button on:click={() => {expanded = experience}}>Ler mais</button>
    </div>
</div>

<style>
    .experience {
        display: flex;
        flex-direction: column;
        align-items: center;
        background-color: white;
        color: black;
        width: min-content;
        border-radius: 20px;
        padding: 10px 30px 30px 30px;
        box-shadow: 3px 3px 0 lightgray;
    }
    
    .itemsExpanded {
        display: flex;
        overflow: hidden;
        flex-direction: column;
        align-items: center;
        text-align: left;
    }

    button {
        display: flex;
        height: 50px;
        width: 150px;
        border-radius: 25px;
        padding: 10px;
        color: white;
        background-color: black;
        box-shadow: 2px 2px lightgray;
        align-items: center;
        justify-content: center;
        text-transform: uppercase;
        font-weight: 600;
        cursor: pointer;
    }
</style>