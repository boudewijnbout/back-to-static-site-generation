<script>
	import Hero from "$lib/components/IndexComponents/Hero.svelte";
	import Introduction from "$lib/components/IndexComponents/Introduction.svelte";
	import Cursor from "$lib/components/Cursor.svelte";
	import StandardSection from "$lib/components/IndexComponents/StandardSection.svelte";
	import Standard from "$lib/components/IndexComponents/Standard.svelte";
	import StandardChapter from "$lib/components/IndexComponents/StandardChapter.svelte";

	export let data;
</script>

<main>
	<Cursor />
	<Hero heroTitle={data.page.title}>
		<Introduction introduction={data.page.introduction} />
	</Hero>
	
	<StandardSection>
		{#each data.standards as standard}
			<Standard
				standardUID={`/${standard.title}`}
				standardTitle={`${standard?.standardnumber}.0 ${standard.title}`}
			>
				{#each standard.chapters as chapter, i}
					<StandardChapter
						chapterTitle={`${standard.standardnumber}.${i + 1} ${
							chapter.data.title
						}`}
						chapterUID={`${chapter.uid}`}
						standardUID={`${standard.title}`}
					/>
				{/each}
			</Standard>
		{/each}
	</StandardSection>
</main>
