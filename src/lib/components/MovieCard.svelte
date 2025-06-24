<script>
  import { favorites } from '$lib/store.js';
  export let movie;

  function addToFavorites() {
    favorites.update(favs => {
      const alreadyAdded = favs.some(f => f.id === movie.id);
      if (!alreadyAdded) {
        alert(`${movie.title} added to favorites!`);
        return [...favs, movie];
      } else {
        alert(`${movie.title} is already in favorites.`);
        return favs;
      }
    });
  }
</script>



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
    <button class="btn btn-outline-warning mt-2" on:click={addToFavorites}>
      ❤️ Add to Favorites
    </button>
  </div>
</div>
