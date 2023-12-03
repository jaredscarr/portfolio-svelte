<script lang="ts">
  import { onMount } from 'svelte';
  import { fly } from 'svelte/transition';
  import { backOut } from 'svelte/easing';


  let animate = false;

  onMount(() => {
    animate = true;
  });
</script>

<svelte:head>
  <title>Home</title>
  <meta name="description" content="jaredscarr.com - portfolio" />
</svelte:head>

<section class="grid grid-cols-1 m-10 mt-20 gap-5 sm:grid-cols-2 sm:gap-10 sm:m-20">
  <div class="m-0 sm:m-20 tracking-wide">
    {#if animate}
    <h2
      class="h2 mb-4 sm:mb-8 tracking-widest font-semibold"
      in:fly={{
      y: 100,
        delay: 500,
        duration: 1000,
        easing: backOut
      }}
    >
      Hello!
    </h2>
    <h5
      class="h5 mb-6 tracking-wide"
      in:fly={{
      y: 100,
        delay: 300,
        duration: 1000,
        easing: backOut
      }}
    >
      My name is
    </h5>
    <h1
      class="h1 mb-8 font-bold tracking-widest text-primary-700-200-token"
      in:fly={{
      y: 100,
        delay: 1000,
        duration: 1000,
        easing: backOut
      }}
    >
      Jared Scarr
    </h1>
    <p class="mb-6 tracking-wide"
      in:fly={{
      y: 100,
        delay: 2000,
        duration: 1000,
        easing: backOut
      }}
    >
      I work as a Software Development Engineer based out of Seattle, Washington.
    </p>
    {/if}
  </div>
  <div class="text-justify m-0 sm:m-20">
    <img class="h-auto max-w-full visible dark:hidden" src="main-image-light.png" alt="Man with laptop">
    <img class="h-auto max-w-full invisible dark:visible" src="main-image-sobel.png" alt="Man with laptop">
  </div>
</section>

<style>

</style>
