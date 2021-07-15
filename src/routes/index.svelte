<script>
	import { pokemon, fetchPokemon } from '../stores/pokestore';
	import Title from '../components/title.svelte';
	import PokemonCard from '../components/pokemon-card.svelte';

	let searchTerm = '';
	let filteredPokemon = [];

	// reactive scope
	$: {
		if (searchTerm) {
			filteredPokemon = $pokemon.filter((pokemon) =>
				pokemon.name.toLowerCase().includes(searchTerm.toLowerCase())
			);
		} else {
			filteredPokemon = [...$pokemon];
		}
	}

  fetchPokemon();
</script>

<svelte:head>
	<title>SvelteKit Pokedex</title>
</svelte:head>

<Title title="SvelteKit Pokedex" />

<input
	bind:value={searchTerm}
	type="search"
	class="w-full rounded-md text-lg p-4 border-2 border-gray-200"
	placeholder="Search Pokemon"
/>

<div class="py-4 grid gap-4 md:grid-cols-2 grid-cols-1">
	{#each filteredPokemon as pokemon}
		<PokemonCard {pokemon} />
	{/each}
</div>
