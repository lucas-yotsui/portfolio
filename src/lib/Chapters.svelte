<script>
    export let chapters;
    export let currentChapter;
</script>

<ol>
    {#each chapters as chapter}
    <a href="#{chapter.name}">
        <li class={currentChapter == chapter.id ? "active" : ""}><div class="line"></div>{chapter.name}</li>
    </a>    
    {/each}
</ol>

<style>
    a {
        color: white;
        text-decoration: none;
    }

    ol {
        list-style: none;
        counter-reset: item;
        font-size: 22px;
        line-height: 34px;
        margin: 0px 0px 0px -40px
    }

    li {
        margin-bottom: 15px;
        display: flex;
        line-height: 60px;
        flex-direction: row;
        font-weight: 300;
        letter-spacing: -0.6px;
    }

    li::before {
        content: counter(item);
        counter-increment: item;
        width: 60px;
        height: 60px;
        border-radius: 50%;
        text-align: center;
        border: solid;
        color: white;
        display: block;
    }

    .line {
        width: 100px;
        border-top: solid white 1px;
        margin: 29px 15px;
    }

    .active {
        font-weight: 500;
    }

    .active::before {
        color: black;
        background: white;
    }

    .active > .line {
        border-top: solid white 4px;
    }
</style>