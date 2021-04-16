<script>
	import Counter from './Counter.svelte';

	let now = new Date();
	let countdownToDate = new Date(2021, 3, 24, 9, 2, 3);

	$: distance = countdownToDate - now;

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

	function toggleSwitch() {
		now = new Date();
	}
</script>

<div class="container" on:click={toggleSwitch}>
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
