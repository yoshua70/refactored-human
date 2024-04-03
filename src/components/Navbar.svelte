<script lang="ts">
  import { onMount } from "svelte";
  import { writable } from "svelte/store";
  import "iconify-icon";

  const darkMode = writable(false);
  let isMenuOpen = false;

  onMount(() => {
    const isDarkMode = localStorage.getItem("darkMode") === "true";
    darkMode.set(isDarkMode);
  });

  $: {
    localStorage.setItem("darkMode", darkMode.toString());
    const body = document.querySelector("body");
    if ($darkMode) {
      body.classList.add("dark");
    } else {
      body.classList.remove("dark");
    }
  }

  function toggleMenu() {
    isMenuOpen = !isMenuOpen;
  }

  console.log(isMenuOpen);
</script>

<nav
  class="p-8 flex flex-col items-center justify-between backdrop-blur-xl fixed top-0 z-10 w-full"
>
  <div class="flex w-full items-center justify-between">
    <div class="flex items-center">
      <a href="/" class="font-bold">Refactored<br />Human</a>
      <ul class="hidden md:flex ml-4 space-x-4">
        <li><a href="/work">Works</a></li>
        <li><a href="/projects">Projects</a></li>
        <li><a href="/blog">Blog</a></li>
        <li>
          <a href="https://github.com/yoshua70.git" target="_blank">Sources</a>
        </li>
      </ul>
    </div>
    <div class="flex items-center">
      <button class="btn" on:click={() => ($darkMode = !$darkMode)}>
        {#if $darkMode}
          <iconify-icon icon="material-symbols-light:light-mode-outline-rounded"
          ></iconify-icon>
        {:else}
          <iconify-icon icon="material-symbols-light:dark-mode-outline-rounded"
          ></iconify-icon>
        {/if}
      </button>
    </div>
    <button class="md:hidden" on:click={toggleMenu}>
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
