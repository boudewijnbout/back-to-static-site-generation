<script>
	import { cursor } from "$lib/stores/cursor";
</script>

<section
	on:mouseleave={() =>
		cursor.set({
			scale: "1",
			color: "rgba(255, 240, 33, 0.5)",
			border: "none",
		})}
>
	<slot />
</section>

<style>
	section {
		padding: 1rem;
		grid-gap: 1rem;
		display: grid;
		border-left: 3px solid var(--color-black);
		border-right: 3px solid var(--color-black);
	}
	@media (min-width: 50rem) {
		section {
			grid-template-columns: 1fr 1fr;
		}
	}
	@media (min-width: 60rem) {
		section {
			grid-template-columns: repeat(4, 1fr);
		}
	}
	@media (min-width: 68.75rem) {
		section {
			padding: 2rem 5rem;
		}
	}
</style>