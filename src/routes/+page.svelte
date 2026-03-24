<script lang="ts">
	import { onMount } from 'svelte';

	let direction = $state('left');

	// track the mouse position and update the direction variable accordingly
	const handleMouseMove = (event: MouseEvent) => {
		const { clientX } = event;
		const windowWidth = window.innerWidth;

		if (clientX < windowWidth / 2) {
			direction = 'left';
		} else {
			direction = 'right';
		}

		console.log(direction);
	};

	onMount(() => {
		window.addEventListener('mousemove', handleMouseMove);

		return () => {
			window.removeEventListener('mousemove', handleMouseMove);
		};
	});
</script>

<div class="main">
	<div class="inner">
		<div class="decide"></div>

		<div class="choices">
			<div class="oranginus">Oranginus</div>

			<div class="man" class:left={direction === 'left'} class:right={direction === 'right'}></div>

			<div class="orangeginus">Orangeginus</div>
		</div>
	</div>
</div>

<style lang="scss">
	.main {
		display: flex;
		align-items: center;
		justify-content: center;

		width: 100%;
		height: 100%;

		background: url('/img/background.jpg') no-repeat center center fixed;
	}

	.inner {
		display: flex;
		flex-direction: column;
	}

	.choices {
		display: flex;
		gap: 3rem;

		.oranginus,
		.orangeginus {
			width: 484px;

			display: flex;
			align-items: center;
			justify-content: center;

			font-family: Alagard;
			font-size: 64px;
			color: #ffa800;
		}

		.man {
			width: 264px;
			height: 328px;

			&.left {
				background: url('/img/point-left.png');
			}

			&.right {
				background: url('/img/point-right.png');
			}
		}
	}
</style>
