<script lang="ts">
	import { resolve } from '$app/paths';
	import { onMount } from 'svelte';

	let choice = $state(0);

	onMount(() => {
		choice = Math.random() < 0.5 ? 1 : 2;
	});
</script>

<svelte:head>
	<title>WRONG</title>
</svelte:head>

<div class="main">
	<div class="inner">
		<div class="wrong"></div>

		<div class={`haha-${choice}`}></div>

		<a class="try-again box-shadow" href={resolve('/')}>try again?</a>
	</div>
</div>

<style lang="scss">
	.main {
		display: flex;
		align-items: center;
		justify-content: center;

		width: 100%;
		height: 100%;

		background: url('/img/background3.jpg') no-repeat center center fixed;
	}

	.inner {
		display: flex;
		flex-direction: column;
		align-items: center;
		gap: 1rem;
	}

	.wrong {
		width: 304px;
		height: 92px;

		background: url('/img/wrong.gif');
	}

	.haha-1 {
		width: 320px;
		height: 240px;

		background: url('/img/f_you.gif');
	}

	.haha-2 {
		width: 320px;
		height: 320px;

		background: url('/img/murderous-emoji-crying-laughing.gif');
		background-size: 320px 320px;
	}

	.try-again {
		font-family: Alagard;
		font-size: 32px;
		color: #000000;
		text-decoration: none;

		border: 4px solid #646464;
		background: #c7c7c7;
		padding: 8px;
	}
</style>
