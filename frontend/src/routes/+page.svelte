<!-- svelte-ignore a11y-img-redundant-alt -->
<script lang="ts">

	const name: string = 'Chacka';
	import image from "../imgs/chacka.jpeg"

	function handleLocationSend() {
		const successCallback = (position: any) => {
			console.log(position);
			const message = `Hi, I found your lost ${name} at https://maps.google.com/?q=${position.coords.latitude},${position.coords.longitude}`;
			window.open(`mailto:hunter@hpe-arch.net?subject=Found%20${name}&body=${message}`);
		};

		const errorCallback = (error: any) => {
		console.log(error);
		};

		navigator.geolocation.getCurrentPosition(successCallback, errorCallback);
	}

</script>

<link rel="preconnect" href="https://fonts.googleapis.com"><link rel="preconnect" href="https://fonts.gstatic.com"><link href="https://fonts.googleapis.com/css2?family=Raleway:wght@100;300&display=swap" rel="stylesheet">

<main>

	<div class="header">

		<h3 class="header-text">Find my friend!</h3>

	</div>

	<div class="image-text-container">
		<h1 class="image-text" style="top: 1rem">Hi, my name is {name}!</h1>
		<!-- svelte-ignore a11y-img-redundant-alt -->
		<img 
			src={image}
		 alt="Can't find my picture right now..." class="friend-pic" />
	</div>

	<div class="address-container">

		<h3 class="address-text">My address:</h3>
		<ul class="address-list">
			<li class="address-list-item">
				<!-- <a href="https://www.google.com/maps/place/123+Main+St,+Anytown,+CA+12345" class="address-link">1081 Lariat Lane, Pebble Beach, CA</a> -->
				<a href="https://www.google.com/maps/place/1081+Lariat+Ln,+Pebble+Beach,+CA+93953" class="address-link">1081 Lariat Lane, Pebble Beach, CA</a>
			</li>
		</ul>
	</div>

	<div class="contact-container">

		<h3 class="contact-text">Contact my family:</h3>
		<ul class="contact-list">
			<li class="contact-list-item">
				<a href="tel:18312776488" class="contact-link">Call my mom</a> (831-277-6488)
			</li>
			<li class="contact-list-item">
				<a href="tel:18312776487" class="contact-link">Call my dad</a> (831-277-6487)
			</li>

		</ul>
		<div class="btn-container">
			<button class="location-btn" on:click={handleLocationSend}>Send your current location</button>
		</div>
	</div>

</main>

<style>

	.btn-container {
		display: flex;
		justify-content: center;
	}

	.location-btn {
		background: rgb(9, 0, 176);
		color: white;
		border: none;
		border-radius: 5px;
		padding: 0.5rem;
		margin-block: 1rem;
	}

	.location-btn:hover {
		box-shadow: 0px 0px 10px black;
	}

	li {
		margin-block: .25rem;
	}

	main {
		background: linear-gradient(0deg, #299ecf, transparent);
		padding-bottom: 1rem;
		font-family: raleway;
	}

	.contact-container, .address-container {
		background: rgb(255 255 255 / 51%);
		margin-inline: 1rem;
		padding-inline: 0.5rem;
		border-radius: 5px;
		padding-bottom: 0.1rem;
		padding-top: 0.1rem;
		margin-top: 2rem;
	}

	.header-text {
		margin: 0;
		color: white;
	}

	.header {
		display: flex;
		justify-content: center;
		padding-block: 1rem;
		background: linear-gradient(90deg, rgba(2,0,36,1) 0%, rgba(9,9,121,1) 0%, rgba(0,212,255,1) 100%);
	}

	.friend-pic {
		max-height: 90vh;
		border-radius: 2rem;
		max-width: 80%;
		margin-top: 1rem;
	}

	.friend-pic:hover {
		filter: grayscale(0%);
	}

	.image-text-container {
		display: flex;
		flex-direction: column;
		align-items: center;
		position: relative
	}

	.image-text {
		font-size: 2rem;
		text-align: center;
		margin: 0;
		white-space: nowrap;
		position: absolute;
		top: 10%;
		left: 50%;
		transform: translate(-50%, -50%);
		color: black;
		background: rgb(255 255 255 / 51%);
		box-shadow: 0px 0px 10px 0 rgb(0 0 0);
		z-index: 2;
		padding-inline: .5rem;
		margin-top: 1rem;
	}

	@media only screen and (min-width: 601px) {
		.address-container, .contact-container {
			margin: 0 auto;
			margin-block: 1rem;
			width: 50%;
		}
	}
	
	/* mobile screen styles */
	@media only screen and (max-width: 600px) {
		.image-text {
			font-size: 1.25rem;
		}


	}

</style>