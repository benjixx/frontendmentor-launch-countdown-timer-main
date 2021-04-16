<script>
	import Counter from './Counter.svelte';
</script>

<div class="container">
	<Counter label="days" value="8" />
	<Counter label="hours" value="23" />
	<Counter label="minutes" value="55" />
	<Counter label="seconds" value="41" />
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
