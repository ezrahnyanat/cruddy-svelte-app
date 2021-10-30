<script>
	const cruddyListHeader = "everything is a cruddy list";
	let list = [];	
	let newItem = "";
	
	function create() {
		list = [...list, newItem]
		newItem = ""
	};
	
	function destroy(index) {
		list.splice(index, 1);
		list = list;
	};
	
	const header = "for 1 loaf";
	const otherHeader = "for 2 loaves";
	const ingredients = [
		{ingredient: "water", amount: 322},
		{ingredient: "starter", amount: 115},
		{ingredient: "flour", amount: 460},
		{ingredient: "salt", amount: 9}
	];
</script>

<section>
	<h2>{cruddyListHeader}</h2>
	<input bind:value={newItem}>
	<button on:click={create}>Create</button>
	{#each list as item, index}
		<ul>
			<li>
				{item} 
				<input bind:value={item}>
				<button on:click={() => destroy(index)}>Delete</button>
			</li>	
		</ul>
	{/each}
</section>

<section>
	<h2>{header}</h2>
	{#each ingredients as {ingredient, amount}}
		<p>{ingredient}: {amount}g</p>
	{/each}
</section>

<section>
	<h2>{otherHeader}</h2>
	{#each ingredients as {ingredient, amount}}
		<p>{ingredient}: {amount * 2}g</p>
	{/each}
</section>

<style>
	section {
		padding: 1em;				
		margin: 1em;
		border: 1px solid black;
		border-radius: 1em;
	}
</style>