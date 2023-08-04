<script>
    import items from "../assets/timeline_items.json";
	import { flip } from "svelte/animate";
	import { slide } from "svelte/transition";
	import { cubicOut } from "svelte/easing";
    
    let hovered;
</script>

<div class="timeline">
    {#each items as item (item.title)}
        <div 
            role="region"
            class="card" 
            on:mouseenter={ () => { hovered = item.title} }
            on:mouseleave={ () => { hovered = ""} }
            animate:flip
        >
        <div class="info">
            <div class="textParts">
                    <h2 class="year">{ item.year }</h2>
                    <h3 class="title">{ item.title }</h3>
                    {#if hovered == item.title && item.text != ""}
                    <p
                        transition:slide={{ duration: 750, easing:cubicOut }}
                    > { item.text } </p>
                    {/if}
                </div>
                <div class="iconOutline">
                    <div class="iconContainer">
                        <img src={ item.icon } alt={ item.title } style="">                
                    </div>
                </div>

            </div>
        </div>    
    {/each}
</div>

<style>
    .timeline {
        display: flex;
        flex-direction: column;
        align-items: center;
        margin: 20px auto;
        padding: 20px;
        width: 500px;
    }
    
    .card {
        display: flex;
        position: relative;
        width: 400px;
        height: 200px;
    }
    
    .card:nth-child(odd) {
        padding: 30px 0 30px 30px;
        justify-content: left;
    }
    
    .card:nth-child(even) {
        padding: 30px 30px 30px 0;
        justify-content: right;
    }

    .card::before {
        content: "";
        position: absolute;
        width: 50%;
        border: solid white;
    }

    .card:nth-child(odd)::before {
        left: 0px;
        top: -4.5px;
        bottom: -4.5px;
        border-width: 5px 0 5px 5px;
        border-radius: 50px 0 0 50px;
    }

    .card:nth-child(even)::before {
        right: 0;
        top: 0;
        bottom: 0;
        border-width: 5px 5px 5px 0;
        border-radius: 0 50px 50px 0;
    }

    .card:first-child::before {
        border-top: 0;
        border-top-left-radius: 0;
    }

    .card:last-child:nth-child(odd)::before {
        border-bottom: 0;
        border-bottom-left-radius: 0;
    }

    .card:last-child:nth-child(even)::before {
        border-bottom: 0;
        border-bottom-right-radius: 0;
    }
    
    .card:last-child:nth-child(odd) > .info > .textParts {
        text-align: left;
    }

    .card:nth-child(even) > .info > .textParts {
        text-align: right;
    }

    .info {
        width: min-content;
    }
    
    img {
        max-width: 60px;
        max-height: 60px;
        aspect-ratio: 1/1;
    }
    
    .iconContainer {
        display: flex;
        align-items: center;
        justify-content: center;
        width: min-content;
        background-color: white;
        padding: 10px;
        border-radius: 50%;
    }
    
    .iconOutline {
        width: min-content;
        height: min-content;
        aspect-ratio: 1 / 1;
        padding: 5px;
        border: solid white 1.5px;
        border-style: dashed;
        border-radius: 50%;
    }

    .info {
        display: flex;
        flex-direction: row;
        align-items: center;
        color: gray;
        border-radius: 10px;
        padding: 10px;
        width: max-content;
    }

    .title {
        color: white;
        position: relative;
        font-weight: 400;
        width: 100%;
    }

    .year {
        margin: 0;
    }

    .info::before {
        content: "";
        position: absolute;
        top: 50%;
        width: 10px;
        height: 10px;
        background: black;
        border-radius: 999px;
        border: 3px solid white;
    }

    .card:nth-child(odd) > .info {
        direction: rtl;
    }
    
    .card:nth-child(odd) > .info > .textParts {
        text-align: left;
    }
    
    .card:nth-child(even) > .info > .textParts {
        text-align: right;
    }
    
    .card:nth-child(odd) > .info::before {
        left: -5px;
    }

    .card:nth-child(even) > .info::before {
        right: -5px;
    }
    
    .card:nth-child(odd) > .info > .iconOutline {
        margin-right: 20px;
    }
    
    .card:nth-child(even) > .info > .iconOutline {
        margin-left: 20px;
    }
</style>