<script lang="ts">
	import { resolve } from '$app/paths';
</script>

<svelte:head>
	<title>The Truth</title>
</svelte:head>

<div class="main">
	<div class="inner">
		<div class="welcome text-shadow">Welcome to the truth!</div>

		<div class="truth-1 text-shadow">
			<div class="img"></div>

			<div class="text">
				"As the owner of this domain, I legally own the rights to the
				<span class="orange">Oranginus</span>
				meme"
				<span class="signature">-Wyatt</span>
			</div>
		</div>

		<div class="truth-2 text-shadow">
			click
			<a href="https://www.youtube.com/channel/UCe06HlT7Cg6Sc9vmrZuLgnw/videos" class="green">
				HERE
			</a>
			for the official
			<span class="orange">Oranginus</span> Youtube!
		</div>

		<div class="truth-3 text-shadow-2">
			<span>
				"I am the TRUE
				<span class="orange">Oranginus</span>"
				<a href={resolve('/bald')} class="signature">-Wyatt</a>
			</span>
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

		background: url('/img/background2.jpg') no-repeat center center fixed;
	}

	.inner {
		display: flex;
		flex-direction: column;
		align-items: center;
		gap: 1.25rem;
	}

	.welcome {
		display: flex;
		align-items: center;
		justify-content: center;

		height: 128px;

		font-family: AltPixelsGoneBad;
		font-size: 40px;
		color: #ffffff;
		text-shadow: 0 0 8px #000000;

		background: url('/img/orange.gif') no-repeat center;
	}

	.truth-1,
	.truth-2,
	.truth-3 {
		font-family: Alagard;
		font-size: 32px;
		color: #ffffff;
		text-align: center;

		.orange {
			color: #ff7a03;
		}

		.green {
			color: #48ff00;
		}
	}

	.truth-1 {
		display: flex;

		.img {
			margin-right: -20px;

			width: 176px;
			height: 215px;

			background: url('/img/top.png');
		}

		.text {
			width: 316px;
		}
	}

	.truth-2 {
		width: 400px;
	}

	.truth-3 {
		display: flex;
		flex-direction: column;
		justify-content: flex-end;

		width: 406px;
		height: 227px;

		background: url('/img/bottom.png') no-repeat;
		background-position: center bottom;

		> span {
			position: relative;
			top: 10px;
		}
	}

	.signature {
		display: block;

		font-size: 22px;
		color: inherit;
		text-align: right;
		text-decoration: none;
	}

	@media (max-width: 768px) {
		.welcome {
			width: 100%;
			max-width: 340px;
			height: 96px;

			font-size: 28px;
			background-size: contain;
		}

		.truth-1,
		.truth-2,
		.truth-3 {
			font-size: 22px;
		}

		.truth-1 {
			.img {
				flex-shrink: 0;
				margin-right: -12px;

				width: 120px;
				height: 147px;

				background-size: contain;
				background-repeat: no-repeat;
			}

			.text {
				width: 220px;
			}
		}

		.truth-2 {
			width: 300px;
		}

		.truth-3 {
			width: 300px;
			height: 168px;

			background-size: contain;
			background-repeat: no-repeat;

			> span {
				top: 5px;
			}
		}

		.signature {
			font-size: 16px;
		}
	}
</style>
