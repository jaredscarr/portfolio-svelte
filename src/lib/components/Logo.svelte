<script lang="ts">
  import { onMount } from "svelte";
  import { fly } from 'svelte/transition';
  import { backOut } from 'svelte/easing';
  import { Bird } from "lucide-svelte";

  let animate = false;
  onMount(() => {
    animate = true;
  });
</script>

{#if animate}
  <div
    class="flex justify-center"
    in:fly={{
      y: 100,
        delay: 100,
        duration: 1500,
        easing: backOut,
      }}
  >
    <Bird />
  </div>
{/if}
