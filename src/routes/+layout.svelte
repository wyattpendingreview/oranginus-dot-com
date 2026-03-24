<script lang="ts">
	import favicon from '$lib/assets/favicon.svg';

	let { children } = $props();
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

{@render children()}

<style lang="scss">
	:global {
		@font-face {
			font-family: Alagard;
			src: url('/font/ALAGARD.TTF') format('truetype');
		}

		@font-face {
			font-family: AltPixelsGoneBad;
			src: url('/font/ALT_PIXELSGONEBAD.TTF') format('truetype');
		}

		body {
			margin: 0;
			padding: 0;
			width: 100vw;
			height: 100vh;

			background: #000000;
		}
	}
</style>
