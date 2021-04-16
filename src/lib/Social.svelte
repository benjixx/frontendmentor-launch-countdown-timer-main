<div class="container">
	<a href="#" class="facebook" />
	<a href="#" class="pinterest" />
	<a href="#" class="instagram" />
</div>

<style>
	.container {
		position: absolute;
		left: 50%;
		bottom: 48px;
		transform: translateX(-50%);

		display: flex;
		gap: 32px;
	}

	.container > * {
		display: block;
		width: 24px;
		height: 24px;
	}

	.facebook,
	.pinterest,
	.instagram {
		background: #8385a9;
		transition: 0.2s background-color ease-in;
	}

	.facebook {
		mask-image: url(/images/icon-facebook.svg);
	}

	.pinterest {
		mask-image: url(/images/icon-pinterest.svg);
	}

	.instagram {
		mask-image: url(/images/icon-instagram.svg);
	}

	.facebook:hover,
	.pinterest:hover,
	.instagram:hover {
		background: #fb5e84;
	}
</style>
