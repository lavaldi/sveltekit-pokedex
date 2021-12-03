<script context="module">
  // this module is for SSR
  import { getPokemonById } from '../../stores/pokestore';
  export async function load(ctx) {
    let id = ctx.page.params.id;
    const pokemon = await getPokemonById(id);
    return { props: { pokemon } };
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
  <img src={pokemon.sprites.other['official-artwork'].front_default} alt={pokemon.name} />
  <table class="table-auto">
    <tbody>
      <tr>
        <th class="text-left">Number</th>
        <td class="pl-3">{pokemon.order}</td>
      </tr>
      <tr>
        <th class="text-left">Type</th>
        <td class="pl-3">
          {pokemon.types.map((t) => t.type.name).join(', ')}
        </td>
      </tr>
      <tr>
        <th class="text-left">Height</th>
        <td class="pl-3">{pokemon.height}</td>
      </tr>
      <tr>
        <th class="text-left">Weight</th>
        <td class="pl-3">{pokemon.weight}</td>
      </tr>
      <tr>
        <th class="text-left">Abilities</th>
        <td class="pl-3">{pokemon.abilities.map((a) => a.ability.name).join(', ')}</td>
      </tr>
    </tbody>
  </table>
</div>
