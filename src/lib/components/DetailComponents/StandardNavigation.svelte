<script>
	import { cursor } from "$lib/stores/cursor";

	export let standardHeaderTitle;
	let isActive = false;

	function toggleMenu() {
		isActive = !isActive;
	}
</script>

<div
	on:mouseenter={() =>
		cursor.set({
			scale: "1.5",
			color: "rgba(0, 0, 0, 0.15)",
			border: "2px dashed #000",
		})}
	on:mouseleave={() =>
		cursor.set({
			scale: "1",
			color: "rgba(255, 240, 33, 0.5)",
			border: "none",
		})}
>
	<strong on:click={toggleMenu}>
		<strong>Inhoud {standardHeaderTitle}</strong>
		{#if isActive}
			<svg
				xmlns="http://www.w3.org/2000/svg"
				class="icon icon-tabler icon-tabler-square-x"
				width="32"
				height="32"
				viewBox="0 0 24 24"
				stroke-width="1.5"
				fill="none"
				stroke-linecap="round"
				stroke-linejoin="round"
			>
				<rect x="4" y="4" width="16" height="16" rx="0" />
				<path d="M10 10l4 4m0 -4l-4 4" />
			</svg>
		{/if}
	</strong>
	<nav class:active={!isActive}>
		<ul>
			<slot />
		</ul>
	</nav>
</div>

<style>
	div {
		background-color: var(--color-cmd-yellow);
		position: fixed;
		bottom: 1rem;
		right: 1rem;
		text-align: left;
		padding: 0.5rem;
		box-shadow: 0 0 3px rgba(0, 0, 0, 0.15);
		display: flex;
		flex-direction: column;
		max-width: 20em;
		z-index: 10;
	}

	strong {
		font-size: 0.8rem;
		cursor: pointer;
		padding: 0 0.15rem;
	}

	svg {
		position: absolute;
		right: -0.25rem;
		top: -2rem;
		stroke: var(--color-black);
		fill: var(--color-cmd-yellow);
	}

	nav {
		display: flex;
		flex-direction: column;
		gap: 1rem;
	}

	nav.active {
		display: none;
	}

	ul {
		display: flex;
		flex-direction: column;
		margin-top: 0.25rem;
	}
</style>
