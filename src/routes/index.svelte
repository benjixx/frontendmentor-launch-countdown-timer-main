<script>
	import Countdown from '$lib/Countdown.svelte';
	import Social from '$lib/Social.svelte';
</script>

<main>
	<h1>We're launching soon</h1>
	<Countdown />
	<Social />
</main>

<style>
	main {
		margin: 0 auto;
		padding-top: 142px;
		width: 327px;
	}

	@media screen and (min-width: 1440px) {
		main {
			padding-top: 132px;
			width: 688px;
		}
	}

	h1 {
		margin-top: 0;
		margin-bottom: 54px;

		font-style: normal;
		font-weight: bold;
		font-size: 18px;
		line-height: 24px;
		text-align: center;
		letter-spacing: 6.13636px;
		text-transform: uppercase;

		color: #ffffff;
	}

	@media screen and (min-width: 1440px) {
		h1 {
			font-size: 22px;
			line-height: 29px;
			letter-spacing: 7.5px;
		}
	}
</style>
