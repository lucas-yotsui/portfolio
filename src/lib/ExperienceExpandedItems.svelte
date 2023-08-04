<script>
    export let size;
    export let data;
</script>

<div 
    class="itemsExpanded"
    style="max-height: { $size * 800 }px; opacity: { $size }"
>
    <ul>
        {#each data.texts as text}
            <li>{ text }</li>
        {/each}
    </ul>    
    
    <button on:click={() => {/*Still working on it*/}}>Ler mais</button>
</div>

<style>
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
    }
</style>