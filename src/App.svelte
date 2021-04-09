<script>
	export let name;
	let count = 0;
	let a = 0;
	function plus1() {
		count += 1;
	}

	function minus1() {
		count -= 1;
	}
	$: console.log(`the count is ${count}`);
	let todos = [
		{ done: false, text: 'make Svelte to do list' },
	];

	function add() {
		todos = todos.concat({ done: false, text: '' });
	}

	function clear() {
		todos = todos.filter(t => !t.done);
	}

	$: remaining = todos.filter(t => !t.done).length;
</script>

<main>
	<h1>Hello {name}!</h1>
</main>

<div class="body">
	<input bind:value={name} />

	{#if count % 2 === 0}
		<p>Even</p>
	{:else}
		<p>Odd</p>
	{/if}
	<p>Total count: {count}</p>
	<button class="countButton" on:click={plus1}> +1 </button>

	<button class="countButton" on:click={minus1}> -1 </button>

	<div class="slider">
		<p>{a}</p>
		<input type="range" bind:value={a} min="0" max="10" />
	</div>
	<div>
	<h1>Todos</h1>

{#each todos as todo}
	<div class:done={todo.done}>
		<input
			type=checkbox
			bind:checked={todo.done}
		>

		<input
			placeholder="What needs to be done?"
			bind:value={todo.text}
		>
	</div>
{/each}

<p>{remaining} remaining</p>

<button on:click={add}>
	Add new
</button>

<button on:click={clear}>
	Clear completed
</button>
</div>

</div>

<style>
	.countButton {
		margin: 30px;
		width: 80px;
	}
	p {
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
	.done {
		opacity: 0.4;
	}
	.body {
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
	.slider {
		border-radius: 25%;
		margin-top: 30px;
		margin-left: 30%;
		margin-right: 30%;
		height: 50px;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>
