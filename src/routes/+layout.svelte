<script>
    import '../app.css';
</script>

<nav class="d-flex justify-content-between p-3 align-items-center" 
      style="background: #1a1a1a; ">
      
      <a href="/" style="color: inherit; text-decoration: none; text-decoration: none;">
  <h2 class="text-white" style="font-family: Quintessential;">🎬 Movie Finder</h2>
  </a>
  <a href="/favorites">
    <button class="btn btn-warning">
      ⭐ Favorites
    </button>
  </a>
  
</nav>
<slot />
