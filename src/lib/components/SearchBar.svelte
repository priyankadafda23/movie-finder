<script>
  export let query = '';
  import { createEventDispatcher } from 'svelte';
  const dispatch = createEventDispatcher();

  const handleKeyPress = (e) => {
    if (e.key === 'Enter') {
      dispatch('search');
    }
  };
</script>

<input
  bind:value={query}
  on:keypress={handleKeyPress}
  placeholder="Search for movies..."
  style="padding: 0.5rem; width: 100%; max-width: 300px; justify-content: center; border-radius: 4px;"
/>
