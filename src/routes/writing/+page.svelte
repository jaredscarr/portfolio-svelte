<script lang="ts">
  import { fly } from 'svelte/transition';
  import { backOut } from "svelte/easing";
  import { onMount } from "svelte";

  const writings = [
    {
      id: 1,
      title: "My First Open Source Contribution",
      url: "https://dev.to/jaredscarr/my-first-open-source-contribution-3j07",
    },
  ]

  let animate = false;
  onMount(() => {
    animate = true;
  });

</script>

<section>
  {#if animate}
  <div class="container max-w-6xl mx-auto px-10 sm:px-100 text-justify">
    <h2 class="h2 mt-20 mb-10 sm:mb-20 font-bold tracking-widest text-primary-700-200-token"
        in:fly={{
      x: -500,
        delay: 100,
        duration: 1500,
        easing: backOut,
      }}
    >
      Writing
    </h2>
    <nav class="list-nav">
      <ul>
        {#each writings as writing}
        <li>
          <a
            href={writing.url}
            data-sveltekit-preload-data="hover"
            target="_blank">
            <span class="flex-auto tracking-wide font-extrabold">{writing.title}</span>
          </a>
        </li>
        {/each}
      </ul>
    </nav>
  </div>
  {/if}
</section>
