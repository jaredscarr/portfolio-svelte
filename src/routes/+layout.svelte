<script lang="ts">
  import '../app.postcss';
  import type { DrawerSettings } from '@skeletonlabs/skeleton';
  import { initializeStores, AppShell, Drawer, AppBar, getDrawerStore, LightSwitch } from "@skeletonlabs/skeleton";
  import { Github, Linkedin, Menu } from "lucide-svelte";

  initializeStores();

  const drawerStore = getDrawerStore();
  const drawerSettings: DrawerSettings = {
    id: 'left-drawer',
    width: 'w-[215px]',
  };

  const currYear = new Date().getFullYear();
</script>

<AppShell>
  <svelte:fragment slot="header">
    <AppBar>
      <svelte:fragment slot="lead">
        <button type="button" class="btn-icon" on:click={() => drawerStore.open(drawerSettings)}>
          <Menu />
        </button>
      </svelte:fragment>
      <div class="invisible sm:visible text-center">
        <h6 class="h6 tracking-widest">Software Development Engineer</h6>
      </div>
      <svelte:fragment slot="trail">
        <LightSwitch />
        <a href="https://github.com/jaredscarr" class="btn-icon" data-sveltekit-preload-data="hover"><Github /></a>
        <a href="https://www.linkedin.com/in/jaredscarr" class="btn-icon" data-sveltekit-preload-data="hover"><Linkedin /></a>
      </svelte:fragment>
    </AppBar>
    <Drawer>
      <nav class="list-nav pl-4 pr-4 mt-4">
        <ul>
          <li><a href="/" data-sveltekit-preload-data="hover" on:click={() => drawerStore.close()}>Home</a></li>
          <li><a href="/about" data-sveltekit-preload-data="hover" on:click={() => drawerStore.close()}>About</a></li>
          <li><a href="/work" data-sveltekit-preload-data="hover" on:click={() => drawerStore.close()}>Work</a></li>
        </ul>
      </nav>
    </Drawer>
  </svelte:fragment>
  <slot />
  <svelte:fragment slot="footer">
    <div class="mt-10 mb-10 text-center">
      <p>Copyright &copy {currYear} Jared Scarr</p>
    </div>
  </svelte:fragment>
</AppShell>
