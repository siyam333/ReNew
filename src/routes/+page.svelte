<script lang="ts">
	import menu from "../lib/menu.svg";
	import car from "../lib/car.jpg";
	import About from "../routes/About.svelte";
	import Footer from "../routes/Footer.svelte";
</script>

<header>
	<div class="menu">
		<img src={menu} alt="menu" />
	</div>
	<div class="t"><p>theme</p></div>
</header>

<main>
	<div class="wrap">
		<div class="imgwrap">
			<img src={car} alt="" />
		</div>
	</div>
</main>

<About />
<Footer />

<style>
	
	
	header {
		position: fixed;
		height: 3em;
		width: 100vw;
		display: flex;
		align-items: center;
		background-color: royalblue;
		z-index: 99999;
	}
	header > div {
		width: 50vw;
	}
	header > div > img {
		height: 2em;
		cursor: pointer;
		margin-left: 1em;
	}
	.t {
		display: grid;
		justify-content: end;
	}
	header > div > p {
		font-size: 1.5em;
		margin: 0;
		margin-right: 1em;
	}
	main {
		font-family: "Oswald", sans-serif;
		display: grid;
		justify-content: center;
		align-items: center;
		padding-top: 3em;
		height: calc(100vh - 3em);
		width: 100vw;
	}
	.wrap {
		display: grid;
		justify-content: center;
		align-items: center;
		height: 90vh;
		width: 90vw;
		border-radius: 5em;
		color: rgb(255, 255, 255);
		overflow: hidden;
	}
	
	.imgwrap {
		height: 90vh;
		width: 90vw;
	}
	.imgwrap > img {
		object-fit: cover;
		height: 100%;
		width: 100%;
		filter: brightness(50%);
	}
</style>
