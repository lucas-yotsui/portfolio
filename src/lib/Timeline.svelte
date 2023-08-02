<script>
    import items from "../assets/timeline_items.json";
</script>

<div class="timeline">
    {#each items as item}
        <div class="card">
            <div class="info">
                <h3 class="title">{ item.title }</h3>
                <div class="iconOutline">
                    <div class="iconContainer">
                        <img src={ item.icon } alt={ item.title } style="">                
                    </div>
                </div>
                <p>{ item.text }</p>

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
    }
    
    .card:nth-child(odd) {
        padding: 30px 0 30px 30px;
        justify-content: left;
    }
    
    .card:nth-child(even) {
        padding: 30px 30px 30px 0;
        justify-content: right;
    }

    /* Global ::before */
    .card::before {
        content: "";
        position: absolute;
        width: 50%;
        border: solid white;
    }

    /* Setting the border of top, bottom, left */
    .card:nth-child(odd)::before {
        left: 0px;
        top: -4.5px;
        bottom: -4.5px;
        border-width: 5px 0 5px 5px;
        border-radius: 50px 0 0 50px;
    }

    /* Setting the border of top, bottom, right */
    .card:nth-child(even)::before {
        right: 0;
        top: 0;
        bottom: 0;
        border-width: 5px 5px 5px 0;
        border-radius: 0 50px 50px 0;
    }

    /* Removing the border if it is the first card */
    .card:first-child::before {
        border-top: 0;
        border-top-left-radius: 0;
    }

    /* Removing the border if it is the last card  and it's odd */
    .card:last-child:nth-child(odd)::before {
        border-bottom: 0;
        border-bottom-left-radius: 0;
    }

    /* Removing the border if it is the last card  and it's even */
    .card:last-child:nth-child(even)::before {
        border-bottom: 0;
        border-bottom-right-radius: 0;
    }
    
    .card:last-child:nth-child(odd) > .info > .title {
        text-align: left;
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

    /* Information about the timeline */
    .info {
        display: flex;
        flex-direction: row;
        align-items: center;
        color: gray;
        border-radius: 10px;
        padding: 10px;
        width: max-content;
    }

    /* Title of the card */
    .title {
        color: white;
        position: relative;
        font-weight: 400;
    }

    /* Timeline dot  */
    .info::before {
        content: "";
        position: absolute;
        top: 80px;
        width: 10px;
        height: 10px;
        background: black;
        border-radius: 999px;
        border: 3px solid white;
    }

    .card:nth-child(odd) > .info {
        direction: rtl;
    }
    /* text right if the card is even  */
    .card:nth-child(even) > .info > .title {
        text-align: right;
    }

    /* setting dot to the left if the card is odd */
    .card:nth-child(odd) > .info::before {
        left: -5px;
    }

    /* setting dot to the right if the card is odd */
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