<script lang="ts">
	import { resolve } from '$app/paths';
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
	};

	onMount(() => {
		window.addEventListener('mousemove', handleMouseMove);

		return () => {
			window.removeEventListener('mousemove', handleMouseMove);
		};
	});
</script>

<svelte:head>
	<title>DECIDE!</title>
</svelte:head>

<div class="main">
	<div class="inner">
		<div class="decide"></div>

		<div class="choices">
			<div class="oranginus text-shadow"><a href={resolve('/oranginus')}>Oranginus</a></div>

			<div class="man" class:left={direction === 'left'} class:right={direction === 'right'}></div>

			<div class="orangeginus text-shadow"><a href={resolve('/orangeginus')}>Orangeginus</a></div>
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
		align-items: center;
	}

	.decide {
		width: 448px;
		height: 119px;
		background: url('/img/DECIDE.png');
	}

	.choices {
		display: flex;
		gap: 3rem;

		.oranginus,
		.orangeginus {
			width: 400px;

			display: flex;
			align-items: center;
			justify-content: center;

			font-family: Alagard;
			font-size: 64px;
			color: #ffa800;

			cursor: pointer;

			a {
				text-decoration: none;
				color: inherit;
			}
		}

		.man {
			width: 264px;
			height: 328px;

			&.left {
				background-image: url('/img/point-left.png');
			}

			&.right {
				background-image: url('/img/point-right.png');
			}
		}
	}

	@media (max-width: 768px) {
		.decide {
			margin-bottom: 1.5rem;

			width: 300px;
			height: 80px;

			background-size: contain;
			background-repeat: no-repeat;
		}

		.choices {
			flex-direction: column;
			align-items: center;
			gap: 1.5rem;

			.oranginus,
			.orangeginus {
				width: auto;
				font-size: 40px;
			}

			.man {
				width: 200px;
				height: 248px;

				background-size: contain;
				background-repeat: no-repeat;
			}
		}
	}
</style>
