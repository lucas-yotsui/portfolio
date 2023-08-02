<script>
	import Experiences from "./lib/Experiences.svelte";
	import Profile from "./lib/Profile.svelte";
	import Timeline from "./lib/Timeline.svelte";
</script>

<div class="leftSide">
	<Profile></Profile>
</div>
<div class="rightSide">
	<section id="Projetos">
		<Experiences></Experiences>
	</section>
	<section id="Formação">
		<Timeline></Timeline>
	</section>
</div>

<style>
	.leftSide {
		margin: 0;
		padding: 0;
		top: 0;
		position: sticky;
		height: min-content;
	}

	.rightSide {
		display: flex;
        flex-direction: column;
        gap: 60px;
		margin: 0;
		padding: 30px 0;
        align-items: center;
        gap: 100px;
	}
</style>