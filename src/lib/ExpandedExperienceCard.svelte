<script>
	import ImgCarrousel from "./ImgCarrousel.svelte";

    export let content;
    export let animate;
</script>

{#if content != null}
    <div 
        class="expandedCard"
        style="transform: translateX({100 - (100 * animate)}px); opacity: {animate}"
    >
        <div 
            class="container"
        >
            <button on:click={() => {content = null}}>&times;</button>
            <h1>{content.title}</h1>
            <div class="contents">
                <div class="imagesAndTopics">
                    <ImgCarrousel
                        contents={ content.imgs }
                        width={ 200 }
                    >
                    </ImgCarrousel>
                    
                    <ul>
                        {#each content.topics as topic}
                            <li>{ topic }</li>
                        {/each}
                    </ul>
                </div>
                
                <span class="separator"></span>
                
                <div class="texts">
                    {#each content.texts as text}
                        <p>{ @html text }</p>
                    {/each}
                </div>
            </div>
        </div>
    </div>
{/if}

<style>
    .expandedCard {
        position: absolute;
        overflow: hidden;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        overflow: none;
        background: rgba(211, 211, 211, 0.2);
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .container {
        background-color: white;
        color: black;
        box-shadow: 3px 3px 0 lightgray;
        width: 80%;
        height: 80%;
        display: flex;
        flex-direction: column;
        align-items: center;
        border-radius: 20px;
        padding: 10px 30px 30px 30px;
    }

    .contents {
        display: flex;
        flex-direction: row;
        align-items: center;
        justify-content: center;
        overflow: hidden;
    }

    .imagesAndTopics {
        display: flex;
        flex-direction: column;
        min-width: 450px;
    }

    .separator {
        height: 70%;
        width: 5px;
        border-radius: 2.5px;
        background-color: grey;
        margin: 0 10px;
    }

    .texts {
        height: 95%;
        width: auto;
        padding: 10px;
        overflow-y: scroll;
    } 

    button {
        position: absolute;
        right: 10%;
        right: 10%;
        height: 50px;
        width: 50px;
        border-radius: 25px;
        padding: 10px;
        font-weight: 400;
        font-size: 40px;
        display: flex;
        color: white;
        background-color: black;
        box-shadow: 2px 2px lightgray;
        align-items: center;
        justify-content: center;
    }
</style>