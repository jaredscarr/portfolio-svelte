<script lang="ts">
  import { fly } from "svelte/transition";
  import { backOut } from "svelte/easing";
  import { onMount } from "svelte";
  import seattleShows from "$lib/assets/seattleShows.png";
  import arcgis from "$lib/assets/arcgis.png";
  import swissTournament from "$lib/assets/swissTournament.png";
  import sandracreative from "$lib/assets/sandracreative.png";
  import northcs from "$lib/assets/northcs.png";
  import workbook from "$lib/assets/workbook.png";
  import conways from "$lib/assets/conways.png";
  import pageReplacement from "$lib/assets/pageReplacement.png";

  const projects = [
    {
      id: 1,
      title: "Seattle Shows Web Scraper",
      url: "https://seattle-shows.jaredscarr.com",
      imgName: seattleShows,
    },
    {
      id: 2,
      title: "Deck.gl Open Source Contribution",
      url: "https://github.com/visgl/deck.gl/pull/8545",
      imgName: arcgis,
    },
    {
      id: 3,
      title: "Swiss Tournament Style API",
      url: "https://github.com/jaredscarr/swiss-tournament",
      imgName: swissTournament,
    },
    {
      id: 4,
      title: "Sandra Creative Artist Blog",
      url: "https://sandracreative.com",
      imgName: sandracreative,
    },
    {
      id: 5,
      title: "Computer Science Club Website",
      url: "https://northcs.org",
      imgName: northcs,
    },
    {
      id: 6,
      title: "Computer Science Club Workbook",
      url: "https://nsccs.github.io/",
      imgName: workbook,
    },
    {
      id: 7,
      title: "Retro Games Open Collaboration",
      url: "https://github.com/nsccs/pygames",
      imgName: conways,
    },
    {
      id: 8,
      title: "Page Replacement Experiment",
      url: "https://github.com/jaredscarr/page-replacement",
      imgName: pageReplacement,
    }
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
      Work
    </h2>
    <p class="mb-10 tracking-wide leading-relaxed">Not all my work is in the public domain. This collection includes open-source contributions, personal projects, and university course work. Thanks for looking!</p>
    <section class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-4 mb-20">
      {#each projects as project}
      <a
        class="block card card-hover p-1"
        href={project.url}
        data-sveltekit-preload-data="hover"
        target="_blank"
      >
        <header class="card-header mb-1">
          <h5 class="h5 text-tertiary-500-400-token">{project.title}</h5>
        </header>
        <section class="p-2 mb-1">
          <img src="{project.imgName}" alt="Project Landing Page">
        </section>
      </a>
      {/each}
    </section>
  </div>
  {/if}
</section>
