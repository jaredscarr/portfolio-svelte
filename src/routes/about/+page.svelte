<script lang="ts">
  import { onMount } from "svelte";
  import { fly } from 'svelte/transition';
  import { backOut } from 'svelte/easing';


  let animate = false;
  onMount(() => {
    animate = true;
  });

</script>

<section>
  <div class="container max-w-6xl mx-auto px-10 sm:px-100 pb-10 mb-10 text-justify">
    {#if animate}
    <h2
      class="h2 mt-20 mb-10 sm:mb-20 font-bold tracking-widest text-primary-700-200-token"
      in:fly={{
      x: -500,
        delay: 100,
        duration: 1500,
        easing: backOut,
      }}
    >
      About Me
    </h2>
    <p class="tracking-wide leading-relaxed">I switched careers after a bootcamp experience in 2016, worked for a few years, then returned to university to complete a computer science degree. I am an active member of the university computer science club and have started a few open source projects for the organization to encourage students at all levels of experience to collaborate in a fun and safe environment. I am eager to learn, build, and mentor others as I navigate the vast and exciting world of technology.
    </p>
    {/if}
  </div>
  <div class="container max-w-sm mx-auto px-10 sm:px-100 pb-20 sm:pb-40">
    <img class="h-auto max-w-full rounded-full" src="head-shot-small.jpg" alt="Head shot of Jared Scarr">
  </div>
</section>
