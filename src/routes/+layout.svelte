<!-- layouts/Layout.svelte -->
<script>
  import { browser } from '$app/environment';
  import { page } from '$app/stores';
  import { webVitals } from '$lib/vitals';
  import { auth } from '../firebase'; // Adjust the path based on your file structure
  import { onMount } from 'svelte';
  import './styles.css';

  /** @type {import('./$types').LayoutServerData} */
  export let data;

  let user;

  onMount(() => {
    const unsubscribe = auth.onAuthStateChanged((authUser) => {
      if (authUser) {
        user = authUser;
      } else {
        user = null;
      }
    });

    return () => unsubscribe();
  });

  $: if (browser && data?.analyticsId) {
    webVitals({
      path: $page.url.pathname,
      params: $page.params,
      analyticsId: data.analyticsId,
    });
  }
</script>

<div class="app">
  <header>
    {#if user}
      <p>Welcome, {user.displayName || user.email}!</p>
    {/if}
    <!-- Other header elements can go here -->
  </header>

  <main>
    <slot />
  </main>

  <footer>
    <!-- Footer content goes here -->
  </footer>
</div>

<style>
  /* Your existing styles remain unchanged */

  .app {
    display: flex;
    flex-direction: column;
    min-height: 100vh;
  }

  main {
    flex: 1;
    display: flex;
    flex-direction: column;
    padding: 1rem;
    width: 100%;
    max-width: 64rem;
    margin: 0 auto;
    box-sizing: border-box;
  }

  footer {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding: 12px;
  }

  footer a {
    font-weight: bold;
  }

  @media (min-width: 480px) {
    footer {
      padding: 12px 0;
    }
  }
</style>
