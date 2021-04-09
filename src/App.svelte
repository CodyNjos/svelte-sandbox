<script>
	export let name;
	let count = 0;

	function plus1() {
		count += 1
	}

	function minus1() {
		count -= 1
	}
	$: console.log(`the count is ${count}`);
</script>

<main>
	<h1>Hello {name}!</h1>
</main>

<style>
	.countButton{
		margin: 30px;
		width: 80px
	}
	p{
		color: white;
		margin: 0px;
		text-align: center;
	}
	main {
		background-color: grey;
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}
	div{
		text-align: center;
		background-color: grey;
		height: 100%;
	}
	h1 {
		color: white;
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


<div >
	<p> Total count: {count} </p>
<button class="countButton" on:click={plus1}>
	+1 
</button>

<button class="countButton" on:click={minus1}>
-1
</button>
{#if count%2 === 0}
<p>Even</p>
{/if}
{#if count%2 != 0}
<p>Odd</p>
{/if}
</div>
