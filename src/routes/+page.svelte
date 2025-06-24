<script>
  import { onMount } from 'svelte';
  import MovieCard from '$lib/components/MovieCard.svelte';
  import SearchBar from '$lib/components/SearchBar.svelte';

  let query = '';
  let results = [];
  let trending = [];
  let loading = false;

  const TMDB_API_KEY = 'dcb198efbcc273867f3b49236e8bc6a1';

  const fetchMovies = async () => {
    if (query.trim().length < 2) return;

    loading = true;
    const url = `https://api.themoviedb.org/3/search/movie?query=${query}&api_key=${TMDB_API_KEY}`;
    const res = await fetch(url);
    const data = await res.json();
    results = data.results ?? [];
    loading = false;
  };

  const fetchTrending = async () => {
    const url = `https://api.themoviedb.org/3/trending/movie/day?api_key=${TMDB_API_KEY}`;
    const res = await fetch(url);
    const data = await res.json();
    trending = data.results ?? [];
  };

  onMount(() => {
    fetchTrending();
  });
</script>

<div class="container" style="justify-content: center; align-items: center; display: flex; flex-direction: column; gap: 20px; padding: 20px;">
  <h1>🎬 Movie Finder</h1>

  <SearchBar bind:query on:search={fetchMovies} />

  {#if loading}
    <p>Loading...</p>
  {:else if results.length > 0}
    <div style="display: flex; flex-wrap: wrap; gap: 12px; justify-content: center;">
      {#each results as movie}
        <MovieCard {movie} />
      {/each}
    </div>
  {:else}
    <h3 class="mt-4">🔥 Trending Movies</h3>
    <div style="display: flex; flex-wrap: wrap; gap: 12px; justify-content: center;">
      {#each trending as movie}
        <MovieCard {movie} />
      {/each}
    </div>
  {/if}
</div>
