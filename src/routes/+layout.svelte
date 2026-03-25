<script lang="ts">
	import favicon from '$lib/assets/favicon.svg';

	let { children } = $props();
	let audioPlaying = $state(false);

	const playAudio = (event: MouseEvent) => {
		const doc = (event.target as HTMLElement).ownerDocument;
		const audio = doc.querySelector('.audio-control > audio') as HTMLAudioElement;

		if (audio.paused) {
			audio.play();
		} else {
			audio.pause();
		}
		audioPlaying = !audio.paused;
	};
</script>

<svelte:head>
	<link rel="icon" href={favicon} />
</svelte:head>

{@render children()}

<div class="audio-control">
	<audio autoplay loop>
		<source
			src="/audio/drone-low-pitched-rotating-growling-ambient-background-effect.mp3"
			type="audio/mpeg"
		/>
	</audio>

	<button onclick={playAudio} aria-label="Toggle audio" class:on={audioPlaying}></button>
</div>

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

		.text-shadow {
			text-shadow:
				0 0 8px #000000,
				0 0 2px #000000;
		}

		.text-shadow-2 {
			text-shadow:
				0 0 8px #000000,
				2px 2px 2px #000000,
				-2px -2px 2px #000000,
				-2px 0 2px #000000,
				2px 0 2px #000000,
				0 -2px 2px #000000,
				0 2px 2px #000000;
		}
	}

	.audio-control {
		position: fixed;
		bottom: 12px;
		right: 12px;

		button {
			width: 70px;
			height: 71px;

			border: 4px solid #646464;
			background: url('/img/off.png');
			background-size: contain;
			cursor: pointer;

			&.on {
				background: url('/img/on.png');
				background-size: contain;
			}
		}
	}
</style>
