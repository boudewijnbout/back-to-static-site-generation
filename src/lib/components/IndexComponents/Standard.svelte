<script>
	export let standardUID;
	export let standardTitle;
	import { cursor } from "$lib/stores/cursor";
</script>

<section>
	<a
		on:mouseenter={() =>
			cursor.set({
				scale: "1.35",
				color: "rgba(0, 0, 0, 0.15)",
				border: "2px dashed #000",
			})}
		on:mouseleave={() =>
			cursor.set({
				scale: "1",
				color: "rgba(255, 240, 33, 0.5)",
				border: "none",
			})}
		href="/">{standardTitle}</a
	>
	<ul><slot /></ul>
</section>

<style>
	a {
		font-size: 1.3rem;
		font-weight: 600;
	}
	ul {
		margin-top: 1rem;
	}
</style>
