<script>
  import { onMount } from 'svelte';
  import { page } from '$app/stores';
  import { favorites } from '$lib/store.js';

  export let data;
  let movie = data.movie;
  const id = $page.params.id;

  onMount(async () => {
    const res = await fetch(`https://api.themoviedb.org/3/movie/${id}?api_key=${import.meta.env.VITE_TMDB_API_KEY}`);
    movie = await res.json();
  });

  function addToFavorites() {
    favorites.update(favs => {
      if (!favs.find(f => f.id === movie.id)) {
        return [...favs, movie];
      }
      return favs;
    });
  }
</script>

{#if movie}
  <div>
    <h2>{movie.title}</h2>
    <img src={`https://image.tmdb.org/t/p/w300${movie.poster_path}`} alt={movie.title} />
    <p>{movie.overview}</p>
    <p><strong>Rating:</strong> {movie.vote_average}</p>
    <button on:click={addToFavorites}>❤️ Add to Favorites</button>
  </div>
{:else}
  <p>Loading movie details...</p>
{/if}
