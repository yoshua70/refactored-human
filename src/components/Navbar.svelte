<script lang="ts">
  import { onMount } from "svelte";
  import { writable } from "svelte/store";
  import "iconify-icon";

  let isMenuOpen = false;

  function toggleMenu() {
    isMenuOpen = !isMenuOpen;
  }

  // let darkMode = true;
  // function handleSwitchDarkMode() {
  //   darkMode = !darkMode;

  //   darkMode
  //     ? document.documentElement.classList.add("dark")
  //     : document.documentElement.classList.remove("dark");
  // }

  console.log(isMenuOpen);
</script>

<nav
  class="p-8 flex flex-col items-center justify-between backdrop-blur-xl fixed top-0 z-10 w-full"
>
  <div class="flex w-full items-center justify-between">
    <div class="flex items-center">
      <a href="/" class="font-bold btn btn-ghost">Refactored<br />Human</a>
      <ul class="hidden md:flex ml-4 space-x-4">
        <li><a href="/work" class="btn btn-ghost">Works</a></li>
        <li><a href="/projects" class="btn btn-ghost">Projects</a></li>
        <li><a href="/blog" class="btn btn-ghost">Blog</a></li>
        <li>
          <a
            href="https://github.com/yoshua70"
            target="_blank"
            class="btn btn-ghost">Sources</a
          >
        </li>
      </ul>
    </div>
    <!-- <div class="flex items-center">
      <button class="btn" on:click={handleSwitchDarkMode}>
        {#if darkMode}
          <iconify-icon icon="material-symbols-light:light-mode-outline-rounded"
          ></iconify-icon>
        {:else}
          <iconify-icon icon="material-symbols-light:dark-mode-outline-rounded"
          ></iconify-icon>
        {/if}
      </button>
    </div> -->
    <button class="btn md:hidden" on:click={toggleMenu}>
      {#if !isMenuOpen}
        <iconify-icon
          icon="material-symbols-light:menu-rounded"
          width="1.5rem"
          height="1.5rem"
        ></iconify-icon>
      {:else}
        <iconify-icon
          icon="material-symbols-light:close-rounded"
          width="1.5rem"
          height="1.5rem"
        ></iconify-icon>
      {/if}
    </button>
  </div>
  {#if isMenuOpen}
    <div class="md:hidden flex w-full items-center">
      <ul class="flex flex-col gap-8 mt-8 items-center justify-center w-full">
        <li><a href="/work">Works</a></li>
        <li><a href="/projects">Projects</a></li>
        <li><a href="/blog">Blog</a></li>
        <li>
          <a href="https://github.com/yoshua70.git" target="_blank">Sources</a>
        </li>
      </ul>
    </div>
  {/if}
</nav>
