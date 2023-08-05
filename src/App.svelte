<script>
	import { onMount } from "svelte";
	import Experiences from "./lib/ExperiencesList.svelte";
	import Profile from "./lib/Profile.svelte";
	import Timeline from "./lib/Timeline.svelte";
	import ExpandedExperienceCard from "./lib/ExpandedExperienceCard.svelte";
	import { tweened } from "svelte/motion";
	import { cubicOut} from "svelte/easing";

	let currentChapter = 1;

	var projectsSection;
	var timelineSection;
	var projectsObserver;
	var timelineObserver;

	let expandedCard = null;
	let animate = tweened(0, {duration: 1000, easing: cubicOut});

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

		return () => { };
	});

	$: {
		(expandedCard != null) ? ($animate = 1) : ($animate = 0);
	}
</script>

{#if expandedCard}
	<div class="expandedCardContainer">
		<ExpandedExperienceCard
			bind:content={expandedCard}
			animate={$animate}
		></ExpandedExperienceCard>
	</div>
{:else}
	<div 
		class="regularContent"
			style="opacity: {1 - $animate}; transform: translateX(-{100 * $animate}px);"
		>
		<div class="leftSide">
			<Profile
				bind:currentChapter={currentChapter}
			></Profile>
		</div>
		<div class="rightSide">
			<section id="Projetos">
				<h2>Meus Projetos</h2>
				<Experiences
					bind:expanded={expandedCard}
				></Experiences>
			</section>
			<section id="Formação">
				<h2>Minha Formação</h2>
				<p
					class="note"
				>
					<i>(Tente colocar o mouse por cima dos itens ou tocar neles para exibir mais detalhes)</i>
				</p>
				<Timeline></Timeline>
			</section>
		</div>
	</div>
{/if}


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
        gap: 25px;
	}

	.rightSide > section::after {
		content: "";
		display: inline-block;
		margin-top: 50px;
		width: 75%;
		height: 2px;
		background: lightgray;
		border-radius: 1px;
	}
	
	.rightSide > section:last-child::after {
		display: none;
	}

	.note {
        display: inline-block;
		width: 60%;
        font-size:smaller;
        color: gray;
    }
</style>