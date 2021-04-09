<script>
	export let name;
	let count = 0;

	function plus1() {
		count += 1
	}

	function minus1() {
		count -= 1
	}
</script>

<main>
	<h1>Hello {name}!</h1>
</main>

<style>
	.countButton{
		text-align: center;
	}
	p{
		text-align: center;
	}
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}
	div{
		text-align: center;
	}
	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>

<p> Total count: {count} </p>
<div >

<button class="countButton" on:click={plus1}>
	+1 
</button>

<button class="countButton" on:click={minus1}>
-1
</button>
</div>