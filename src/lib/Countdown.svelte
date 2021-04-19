<script>
	import { onMount } from 'svelte';

	import Counter from './Counter.svelte';

	function getRandomIntInclusive(min, max) {
		min = Math.ceil(min);
		max = Math.floor(max);
		return Math.floor(Math.random() * (max - min + 1)) + min;
	}

	let now = new Date();
	const countdownToDate = new Date(
		now.getTime() + getRandomIntInclusive(1000 * 60, 1000 * 60 * 60 * 24 * 7)
	);

	$: distance = countdownToDate - now > 0 ? countdownToDate - now : 0;

	$: days = Math.floor(distance / (1000 * 60 * 60 * 24))
		.toString()
		.padStart(2, '0');
	$: hours = Math.floor((distance % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60))
		.toString()
		.padStart(2, '0');
	$: minutes = Math.floor((distance % (1000 * 60 * 60)) / (1000 * 60))
		.toString()
		.padStart(2, '0');
	$: seconds = Math.floor((distance % (1000 * 60)) / 1000)
		.toString()
		.padStart(2, '0');

	onMount(() => {
		const interval = setInterval(() => {
			now = new Date();
		}, 1000);

		return () => clearInterval(interval);
	});
</script>

<div class="container">
	<Counter label="days" value={days} />
	<Counter label="hours" value={hours} />
	<Counter label="minutes" value={minutes} />
	<Counter label="seconds" value={seconds} />
</div>

<style>
	.container {
		display: flex;
		gap: 16px;
	}

	@media screen and (min-width: 1440px) {
		.container {
			gap: 32px;
		}
	}
</style>
