<script>
  import { favorites } from '$lib/store.js';
  import { onDestroy } from 'svelte';

  let favs = [];

  const unsubscribe = favorites.subscribe(value => {
    favs = value;
  });

  onDestroy(unsubscribe);
</script>
<div class="container" style="justify-content: center; align-items: center; display: flex; flex-direction: column; gap: 20px; padding: 20px;">
<h1>Your Favorite Movies</h1>

{#if favs.length > 0}
  <div class="d-flex flex-wrap gap-3 justify-content-start">
    {#each favs as movie}
      <div class="card bg-dark text-white p-2 movie-card" style="width: 180px; min-height: 420px;">
        <img
          src={"https://image.tmdb.org/t/p/w300" + movie.poster_path}
          alt={movie.title}
          class="card-img-top"
          style="height: 300px; border-radius: 4px;"
        />
        <div class="card-body p-1">
          <h6 class="card-title fw-bold">{movie.title}</h6>
          <p class="card-text">
            ⭐ {movie.vote_average.toFixed(3)} / 10
          </p>
        </div>
      </div>
    {/each}
  </div>
{:else}
  <p>No favorite movies added yet.</p>
{/if}

</div>