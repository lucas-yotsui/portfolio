<script>
    import ImgCarrousel from "./ImgCarrousel.svelte";
	import ExperienceExpandedItems from "./ExperienceExpandedItems.svelte";
    import experiencesData from "../assets/experiences.json";
	import { cubicInOut } from "svelte/easing";
	import { tweened } from "svelte/motion";
	import { beforeUpdate } from "svelte";

    let experiences = [];
    
    beforeUpdate(() => {
        for (var experience of experiencesData) {
            experiences.push(
                {
                    data: experience,
                    size: tweened(0, {
                        duration: 800,
                        easing: cubicInOut
                    })
                }
            );
        }

        return () => {};
    });
</script>

<div class="experiencesList">
    {#each experiences as experience}
        <div 
            role="region"
            class="experience"
            on:mouseenter={(e) => { experience.size.set(1) }}
            on:mouseleave={(e) => { experience.size.set(0) }}
        >
            <h1>{ experience.data.title }</h1>
        
            <ImgCarrousel
                contents={ experience.data.imgs }
                width={ 200 }
            >
            </ImgCarrousel>
            
            <ExperienceExpandedItems
                size={ experience.size }
                data={ experience.data }
            ></ExperienceExpandedItems>
        </div>
    {/each}
</div>

<style>
    .experiencesList {
        display: flex;
        flex-direction: column;
        gap: 30px;
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
</style>