<script>
  let count = 0;
  let svelteFeatures = [
    'Reactive declarations',
    'Component-scoped CSS',
    'Truly reactive framework',
    'Compile-time framework',
    'No virtual DOM',
    'Simple and intuitive syntax'
  ];

  // Reactive declarations in Svelte
  $: doubleCount = count * 2;

  function increment() {
    count += 1;
  }

  // Lifecycle function similar to useEffect
  import { onMount } from 'svelte';

  onMount(() => {
    console.log('Component mounted');
    return () => console.log('Component unmounted');
  });
</script>

<style>
  /* You can include any additional custom styles here if necessary */
</style>

<div class="min-h-screen flex flex-col items-center justify-center bg-gradient-to-br from-orange-50 to-red-100 p-4">
  <div class="bg-white bg-opacity-80 mt-5 backdrop-blur-lg rounded-2xl shadow-xl p-8 w-full max-w-md">
    <h1 class="text-3xl font-light text-gray-800 mb-6 text-center">Svelte Concepts</h1>
    <div class="space-y-6">
      <p class="text-center">
        <span class="text-4xl font-extralight text-gray-700">{count}</span>
        <span class="text-sm text-gray-500 ml-2">({doubleCount} doubled)</span>
      </p>
      <button on:click={increment} class="w-full px-6 py-2 bg-gradient-to-r from-orange-400 to-red-500 text-white rounded-full hover:opacity-90 transition-opacity focus:outline-none focus:ring-2 focus:ring-red-300">
        Increment
      </button>
      <div class="mt-8">
        <h2 class="text-xl font-semibold text-gray-700 mb-3">Svelte Features</h2>
        <ul class="space-y-2">
          {#each svelteFeatures as feature}
            <li class="flex items-center text-gray-600">
              <svg class="h-4 w-4 mr-2 text-orange-500" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M13 7l5 5m0 0l-5 5m5-5H6" />
              </svg>
              {feature}
            </li>
          {/each}
        </ul>
      </div>
    </div>
  </div>
  <footer class="mt-8 text-sm text-gray-500">
    Made with ❤️ and Svelte.
  </footer>
</div>