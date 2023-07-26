<script lang="ts">
  import "@fontsource-variable/mulish";
  import "../app.css";

  import GlobalFooter from "src/components/GlobalFooter.svelte";

  import GTagManagerScript from "src/components/GTagManagerScript.svelte";
  import Header from "src/components/Header.svelte";
  import { fade } from "svelte/transition";

  export let data: any;

  const { categories } = data || {};
</script>

<GTagManagerScript />

<Header {categories} />
<main class="main-wrapper min-h-[70vh] py-20" in:fade={{ delay: 0 }}>
  <slot />
</main>
<GlobalFooter />

<style lang="scss">
  :global(:root) {
    --primary-color: #0498b4;
    --primary-background-color: #f5f5f5;
    --text-black: #191a1c;
    --text-grey: #252526;
    --secondary-background-color: #f2f2f2;
    --input-box-shadow: 0 0 3px rgba(0, 0, 0, 0.2);
    --skeleton-background-grey: #e0e0e0;
    --input-border-grey: #d4d4d4;
  }

  :global(body),
  :global(html) {
    margin: 0;
    padding: 0;
  }

  :global(html) {
    font-size: 62.5%;
    font-family: "Mulish Variable", Geneva, Tahoma, sans-serif;

    @media (max-width: 768px) {
      font-size: 50%;
    }
  }
  :global(body) {
    line-height: 1.5;
    color: var(--text-black);
    background-color: var(--primary-background-color);
  }

  .main-wrapper {
    padding-top: 100px;
  }
</style>
