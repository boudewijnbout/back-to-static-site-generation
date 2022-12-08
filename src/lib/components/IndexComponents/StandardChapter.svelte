<script>
	export let standardUID;
	export let chapterUID;
	export let chapterTitle;
	import { cursor } from "$lib/stores/cursor";
	const path = standardUID.toLowerCase().split(" ").join("-");
</script>

<li>
	<a
		on:mouseenter={() =>
			cursor.set({
				scale: "1.1",
				color: "rgba(0, 0, 0, 0.15)",
				border: "2px dashed #000",
			})}
		on:mouseleave={() =>
			cursor.set({
				scale: "1",
				color: "rgba(255, 240, 33, 0.5)",
				border: "none",
			})}
		href="{path}#{chapterUID}">{chapterTitle}</a
	>
</li>

<style>
	li {
		list-style-type: none;
	}
	a {
		padding: 0.5rem 0;
		color: var(--color-black);
	}
</style>