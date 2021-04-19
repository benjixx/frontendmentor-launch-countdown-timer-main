<script>
	import { afterUpdate } from 'svelte';

	export let label;
	export let value;

	let previousValue = null;
	let newValueTop = null;
	let newValueBottom = null;

	let counterTopPreviousRef;
	let counterBottomRef;

	afterUpdate(() => {
		if (previousValue === null) {
			previousValue = value;
			newValueBottom = value;
			newValueTop = value;
		}

		const valueChanged = value !== previousValue;

		if (valueChanged) {
			const timeline = gsap.timeline();
			timeline
				.set(counterTopPreviousRef, { transformOrigin: 'bottom' })
				.set(counterBottomRef, { transformOrigin: 'top', rotateX: 90 })
				.call(() => {
					newValueBottom = value;
					newValueTop = value;
				})
				.to(counterTopPreviousRef, { duration: 0.5, rotateX: -90, ease: 'power1.in' })
				.to(counterBottomRef, { duration: 0.4, rotateX: 0, ease: 'power3.out' })
				.call(() => {
					previousValue = value;
				})
				.set(counterTopPreviousRef, { rotateX: 0 });
		}
	});
</script>

<div class="container">
	<div class="counter">
		<div class="counter-top-previous" bind:this={counterTopPreviousRef}>
			<div class="counter-top-value">{previousValue}</div>
		</div>
		<div class="counter-top">
			<div class="counter-top-value">{newValueTop}</div>
		</div>
		<div class="counter-bottom" bind:this={counterBottomRef}>
			<div class="counter-bottom-value">{newValueBottom}</div>
		</div>
		<div class="counter-bottom-previous">
			<div class="counter-bottom-value">{previousValue}</div>
		</div>
		<div class="counter-background" />
	</div>
	<div class="label">{label}</div>
</div>

<style>
	.container {
		--counter-top-color: #e74e7b;
		--counter-bottom-color: #ff5b8f;
		--counter-top-background-color: #31354f;
		--counter-bottom-background-color: #3a3f5c;

		display: flex;
		flex-direction: column;
		align-items: center;
		gap: 13px;
	}

	@media screen and (min-width: 1440px) {
		.container {
			gap: 19px;
		}
	}

	.counter {
		position: relative;

		display: grid;
		grid-template:
			'top' 33px
			'bottom' 33px / 70px;

		font-size: 36px;
		line-height: 71px;
		font-weight: 700;
	}

	@media screen and (min-width: 1440px) {
		.counter {
			grid-template:
				'top' 70px
				'bottom' 70px / 148px;

			font-size: 80px;
			letter-spacing: -2.4px;
		}
	}

	.counter-top,
	.counter-top-previous,
	.counter-bottom,
	.counter-bottom-previous {
		overflow: hidden;

		display: flex;
		flex-direction: column;
		align-items: center;

		backface-visibility: hidden;
		transform-style: preserve-3d;
	}

	.counter-top,
	.counter-top-previous {
		--scoop-radius: 3px;

		grid-area: top;
		border-radius: 4px 4px 0 0;
		background: var(--counter-top-background-color);

		mask: radial-gradient(circle at 0 100%, transparent var(--scoop-radius), #000 0),
			radial-gradient(circle at 100% 100%, transparent var(--scoop-radius), #000 0);
		mask-composite: intersect;
	}

	.counter-bottom,
	.counter-bottom-previous {
		--scoop-radius: 3px;

		grid-area: bottom;
		border-top: 0.15px solid rgba(0, 0, 0, 0.15);
		border-radius: 0 0 4px 4px;
		background: var(--counter-bottom-background-color);

		mask: radial-gradient(circle at 0 0, transparent var(--scoop-radius), #000 0),
			radial-gradient(circle at 100% 0, transparent var(--scoop-radius), #000 0);
		mask-composite: intersect;
	}

	.counter-top-previous,
	.counter-bottom {
		z-index: 1;
	}

	.counter-top,
	.counter-top-previous {
		box-shadow: 0 -1px 2px #1d1e28;
	}

	.counter-bottom,
	.counter-bottom-previous {
		box-shadow: 0 1px 2px #1d1e28;
	}

	@media screen and (min-width: 1440px) {
		.counter-top,
		.counter-top-previous {
			--scoop-radius: 6px;
			border-radius: 8px 8px 0 0;
		}

		.counter-bottom,
		.counter-bottom-previous {
			--scoop-radius: 6px;
			border-radius: 0 0 8px 8px;
		}
	}

	/* debug */
	/* .counter-top-previous,
	.counter-bottom-previous {
		background: red;
	} */

	.counter-top-value {
		color: var(--counter-top-color);
		transform: translateY(-3px);
	}

	.counter-bottom-value {
		color: var(--counter-bottom-color);
		transform: translateY(-36px);
	}

	@media screen and (min-width: 1440px) {
		.counter-top-value {
			transform: translateY(34px);
		}
	}

	.counter-background {
		position: absolute;
		left: 0%;
		right: 0%;
		top: 0%;
		bottom: 0%;

		background: #191a23;
		border-radius: 8px;

		transform: translateY(4px);

		z-index: -1;
	}

	@media screen and (min-width: 1440px) {
		.counter-background {
			transform: translateY(10px);
		}
	}

	.label {
		font-weight: bold;
		font-size: 7px;
		line-height: 9px;
		text-align: center;
		letter-spacing: 2.95937px;

		color: #8385a9;
		text-transform: uppercase;
	}

	@media screen and (min-width: 1440px) {
		.label {
			font-size: 14px;
			line-height: 19px;
			letter-spacing: 5.91875px;
		}
	}
</style>
