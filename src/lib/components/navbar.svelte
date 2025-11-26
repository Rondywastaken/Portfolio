<script lang="ts">
  import { onMount } from "svelte";
  import { page } from "$app/stores";

  let isDark = $state(false);

  const setTheme = (dark: boolean) => {
    isDark = dark;
    document.documentElement.dataset["theme"] = dark ? 'dark' : 'light';
    localStorage.setItem('theme', dark ? 'dark' : 'light');
  };

  const checkActive = (path: string) => {
    if(path == $page.url.pathname) {
      return true;
    }
    return false;
  }

  onMount(() => {
    const savedTheme = localStorage.getItem('theme');
    const systemDark = window.matchMedia("(prefers-color-scheme: dark)").matches;
    setTheme(savedTheme ? savedTheme === 'dark' : systemDark);
  });
</script>

<nav>
  <a href="/" class="navbar-elements" class:active={checkActive("/")}>
    Home</a>
  <a href="/projects" class="navbar-elements" class:active={checkActive("/projects")}>
    Projects</a>
  <a href="/contact" class="navbar-elements" class:active={checkActive("/contact")}>
    Contact</a>
</nav>
{#if !isDark}
  <i onclick={() => setTheme(true)} class="fa-solid fa-moon theme-btn"></i>
{:else}
  <i onclick={() => setTheme(false)} class="fa-solid fa-sun theme-btn"></i> 
{/if}

