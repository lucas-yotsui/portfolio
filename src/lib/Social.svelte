<script>
    export let socialProfiles;
</script>

<div class="buttonsContainer">
    {#each socialProfiles as profile}
        <a class="socialButton" href={profile.url}>
            <img src={profile.src} alt={profile.name}>
            <span>{profile.name}</span>
            <img src="./images/link.svg" alt="Open link" class="link">
        </a>
    {/each}
</div>

<style>
    .buttonsContainer {
        display: flex;
        flex-direction: row;
        justify-content: space-between;
    }

    .socialButton {
        margin-right: 55px;
        cursor: pointer;
        display: flex;
        align-items: center;
    }

    .socialButton:hover {
        -webkit-animation: text3d 750ms infinite;
        animation: text3d 750ms infinite;
    }

    .socialButton:hover img{
        -webkit-animation: img3d 750ms infinite;
        animation: img3d 750ms infinite;
    }

    @keyframes text3d {
        0% {
            text-shadow: 1px 0.5px #f44336, -1px -0.75px #2196f3;
        }
        
        25% {
            text-shadow: 1px -0.5px #f44336, -1px 0.75px #2196f3;
        }
        
        50% {
            text-shadow: -1px -0.5px #f44336, 1px 0.75px #2196f3;
        }
        
        75% {
            text-shadow: -1px 0.5px #f44336, 1px -0.75px #2196f3;
        }

        100% {
            text-shadow: 1px 0.5px #f44336, -1px -0.75px #2196f3;
        }
    }

    @keyframes img3d {
        0% {
            filter: drop-shadow(1px 0.5px #f44336) drop-shadow(-1px -0.75px #2196f3);
        }
        
        25% {
            filter: drop-shadow(1px -0.5px #f44336) drop-shadow( -1px 0.75px #2196f3);
        }
        
        50% {
            filter: drop-shadow(-1px -0.5px #f44336) drop-shadow(1px 0.75px #2196f3);
        }
        
        75% {
            filter: drop-shadow(-1px 0.5px #f44336) drop-shadow( 1px -0.75px #2196f3);
        }

        100% {
            filter: drop-shadow(1px 0.5px #f44336) drop-shadow(-1px -0.75px #2196f3);
        }
    }

    img {
        margin: 0 9px 0 0;
        width: 28px;
    }

    .link {
        margin: 0 0 0 4px;
        width: 15px;
    }

    span {
        font-size: 15px;
        font-weight: 700;
        color: white;
        text-decoration: underline;
    }
</style>