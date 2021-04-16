<script>
	export let label;
	export let value;
</script>

<div class="container">
	<div class="counter">
		<div class="counter-top">
			<div class="counter-top-value">{value}</div>
		</div>
		<div class="counter-bottom">
			<div class="counter-bottom-value">{value}</div>
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
		gap: 9px;
	}

	@media screen and (min-width: 1440px) {
		.container {
			gap: 16px;
		}
	}

	.counter {
		position: relative;

		display: flex;
		flex-direction: column;
		align-items: center;

		width: 70px;
		height: 71px;

		font-size: 36px;
		line-height: 71px;
		font-weight: 700;
	}

	@media screen and (min-width: 1440px) {
		.counter {
			width: 148px;
			height: 150px;

			font-size: 80px;
			letter-spacing: -2.4px;
		}
	}

	.counter-top,
	.counter-bottom {
		width: 100%;
		height: 46.5%;
		overflow: hidden;

		display: flex;
		flex-direction: column;
		align-items: center;
	}

	.counter-top {
		border-bottom: 0.15px solid rgba(0, 0, 0, 0.15);
		border-radius: 4px 4px 0 0;
		background: var(--counter-top-background-color);
	}

	.counter-bottom {
		border-top: 0.15px solid rgba(0, 0, 0, 0.15);
		border-radius: 0 0 4px 4px;
		background: var(--counter-bottom-background-color);
	}

	@media screen and (min-width: 1440px) {
		.counter-top {
			border-radius: 8px 8px 0 0;
		}

		.counter-bottom {
			border-radius: 0 0 8px 8px;
		}
	}

	.counter-top-value {
		color: var(--counter-top-color);
		transform: translateY(-2px);
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

		z-index: -1;
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
