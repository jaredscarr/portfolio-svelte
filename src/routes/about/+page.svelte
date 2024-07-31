<script lang="ts">
  import { onMount } from "svelte";
  import { fly } from "svelte/transition";
  import { backOut } from "svelte/easing";
  import ConnectButton from "$lib/ConnectButton.svelte";
  import headshot from "$lib/assets/headshot.jpg";

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
    <p class="tracking-wide leading-relaxed mb-10">I am a dedicated and versatile Software Developer with a passion for creating impactful solutions through technology. With over three years of experience, I've honed my skills in building MVC web applications, Python scripting, and ETL processes. My technical toolkit includes proficiency in Python, Java, and client-side JavaScript, along with expertise in a variety of frameworks and tools.
    </p>
    <p class="tracking-wide leading-relaxed mb-20">
      With a strong foundation in both theory and practical application, I thrive in collaborative environments where I can contribute my skills and continue to learn. Let's connect and explore how we can work together!
    </p>
    <div class="container text-center">
      <ConnectButton />
    </div>
    {/if}
  </div>
  <div class="container max-w-sm mx-auto px-10 sm:px-100 pb-20 sm:pb-40">
    <img class="h-auto max-w-full rounded-full" src={headshot} alt="Head shot of Jared Scarr">
  </div>
</section>
