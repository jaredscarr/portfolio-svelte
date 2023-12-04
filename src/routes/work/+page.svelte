<script lang="ts">
  import Logo from '$lib/components/Logo.svelte';
  import { fly } from 'svelte/transition';
  import { backOut } from "svelte/easing";
  import { onMount } from "svelte";
  import { ArrowBigRight, ArrowBigLeft } from "lucide-svelte";


  const projects = [
    {
      id: 1,
      title: "Sandra Creative Artist Blog",
      url: "https://sandracreative.com",
      imgUrl: "sandracreative.png",
    },
    {
      id: 2,
      title: "Computer Science Club Website",
      url: "https://northcs.org",
      imgUrl: "northcs.png",
    },
    {
      id: 3,
      title: "Computer Science Club Workbook",
      url: "https://nsccs.github.io/",
      imgUrl: "workbook.png",
    },
    {
      id: 4,
      title: "Retro Games Open Collaboration",
      url: "https://github.com/nsccs/pygames",
      imgUrl: "conways.png",
    },
    {
      id: 5,
      title: "Page Replacement Experiment",
      url: "https://github.com/jaredscarr/page-replacement",
      imgUrl: "page-replacement.png",
    },
    {
      id: 6,
      title: "Swiss Tournament Style API",
      url: "https://github.com/jaredscarr/swiss-tournament",
      imgUrl: "swiss-tournament.png",
    }
  ]

  let animate = false;
  onMount(() => {
    animate = true;
  });


  let elemProjects: HTMLDivElement;

  function multiColumnLeft(): void {
    let x = elemProjects.scrollWidth;
    if (elemProjects.scrollLeft !== 0) x = elemProjects.scrollLeft - elemProjects.clientWidth;
    elemProjects.scroll(x, 0);
  }

  function multiColumnRight(): void {
    let x = 0;
    // -1 is used because different browsers use different methods to round scrollWidth pixels.
    if (elemProjects.scrollLeft < elemProjects.scrollWidth - elemProjects.clientWidth - 1) x = elemProjects.scrollLeft + elemProjects.clientWidth;
    elemProjects.scroll(x, 0);
  }


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
      Work
    </h2>
    <p class="mb-10 tracking-wide leading-relaxed">Not all my work is in the public domain. This is collection of my personal work that includes applications, group projects, university course work, and documentation. Thanks for looking!</p>

    <div class="grid grid-cols-[auto_1fr_auto] gap-4 items-center">
      <button type="button" class="btn-icon variant-filled" on:click={multiColumnLeft}>
        <ArrowBigLeft />
      </button>
      <!-- Carousel -->
      <div bind:this={elemProjects} class="snap-x snap-mandatory scroll-smooth flex gap-2 pb-2 overflow-x-auto mb-20">
        {#each projects as project}
          <div class="snap-start shrink-0 card-hover variant-glass-surface py-0 w-44 md:w-80 text-center">
            <header class="card-header mb-1">
              <h5 class="h5 text-tertiary-500-400-token">{project.title}</h5>
            </header>
            <section class="p-2 mb-2">
              <img src="{project.imgUrl}" alt="Project Landing Page">
            </section>
            <footer class="card-footer text-right">
              <a
                class="btn variant-filled-secondary rounded-full"
                href="{project.url}"
                data-sveltekit-preload-data="hover"
                target="_blank"
              >
                Check it Out!
              </a>
            </footer>
          </div>
        {/each}
      </div>
      <button type="button" class="btn-icon variant-filled" on:click={multiColumnRight}>
        <ArrowBigRight />
      </button>
    </div>
  </div>
  {/if}
  <Logo />
</section>
