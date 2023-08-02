<script>
	import { onMount } from "svelte";
	import Experiences from "./lib/Experiences.svelte";
	import Profile from "./lib/Profile.svelte";
	import Timeline from "./lib/Timeline.svelte";

	let currentChapter = 1;

	var projectsSection;
	var timelineSection;
	var projectsObserver;
	var timelineObserver;

	onMount(() => {
		projectsSection = document.getElementById("Projetos");
		timelineSection = document.getElementById("Formação");

		projectsObserver = new IntersectionObserver((entries, observer) => {
			entries.forEach((entry) => {
				if(entry.isIntersecting) {
					currentChapter = 1;
				}
			});
		}, {
			root: null,
			threshold: 0.1
		});
		
		timelineObserver = new IntersectionObserver((entries, observer) => {
			entries.forEach((entry) => {
				if(entry.isIntersecting) {
					currentChapter = 2;
				}
			});
		}, {
			root: null,
			threshold: 0.1
		});

		projectsObserver.observe(projectsSection);
		timelineObserver.observe(timelineSection);
	});
</script>

<div class="leftSide">
	<Profile
		bind:currentChapter={currentChapter}
	></Profile>
</div>
<div class="rightSide">
	<section id="Projetos">
		<h2>Meus Projetos</h2>
		<Experiences></Experiences>
	</section>
	<section id="Formação">
		<h2>Minha Formação</h2>
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
		text-align: center;
        gap: 100px;
	}
</style>