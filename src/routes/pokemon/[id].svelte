<script context="module">
  // this module is for SSR
  import { getPokemonById } from '../../stores/pokestore';
  export async function load(ctx) {
    let id = ctx.page.params.id;
    const pokemon = await getPokemonById(id);
    return { props: { pokemon }}
  }
</script>

<script>
    export let pokemon;
    const type = pokemon.types[0].type.name;
</script>

<svelte:head>
	<title>{pokemon.name} - SvelteKit Pokedex</title>
</svelte:head>

<div class="flex flex-col items-center">
  <h1 class="text-4xl text-center my-8 uppercase">{pokemon.name}</h1>
  <p>Type: <strong>{type}</strong> | Height: <strong>{pokemon.height}</strong>
    | Weight: <strong>{pokemon.weight}</strong>
  </p>
  <img class="card-image" src={pokemon.sprites['front_default']} alt={pokemon.name} />
</div>