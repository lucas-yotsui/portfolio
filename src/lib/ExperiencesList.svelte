<script>
    import experiences from "../assets/experiences.json";
	import Experience from "./Experience.svelte";

    export let expanded = null;
</script>

<div class="experiencesList">
    {#each experiences as experience (experience.id)}
        <Experience
            {experience}
            bind:expanded={expanded}
        >
        </Experience>
    {/each}
</div>

<style>
    .experiencesList {
        display: flex;
        flex-direction: column;
        gap: 30px;
    }
</style>