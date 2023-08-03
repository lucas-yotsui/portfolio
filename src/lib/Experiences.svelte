<script>
	import ImgCarrousel from "./ImgCarrousel.svelte";
    import experiences from "../assets/experiences.json";
	import { fade, fly } from "svelte/transition";
	import { sineIn } from "svelte/easing";

    let hovered;

    function expandCard(name) {

    }
</script>

<div class="experiencesList">
    {#each experiences as experience (experience.title)}
        <div 
            role="region"
            class="experience" 
            on:mouseenter={(e) => { hovered = experience.title; }}
            on:mouseleave={(e) => { hovered = ""; }}
        >
            <h1>{ experience.title }</h1>
        
            <ImgCarrousel
                contents={ experience.imgs }
                width={ 200 }
            >
            </ImgCarrousel>
            
            {#if hovered == experience.title}
                <div 
                    class="itemsExpanded" 
                    transition:fade={{ duration:500, easing: sineIn}}
                >
                    <ul>
                        {#each experience.texts as text}
                            <li>{ text }</li>
                        {/each}
                    </ul>    
                    
                    <button on:click={(e) => expandCard(experience.title)}>Ler mais</button>
                </div>
            {/if}
        </div>
    {/each}
</div>

<style>
    .experiencesList {
        display: flex;
        flex-direction: column;
        gap: 30px;
    }

    .itemsExpanded {
        display: flex;
        flex-direction: column;
        align-items: center;
        text-align: left;
    }    
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
    }
</style>