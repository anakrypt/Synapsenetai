<script lang="ts">
  import { theme } from "../../lib/theme";

  function toggle() {
    theme.toggle();
  }
</script>

<button class="theme-toggle" on:click={toggle} title="Toggle theme">
  {#if $theme === "dark"}
    <span class="toggle-dot dark-active"></span>
    <span class="toggle-label">DARK</span>
  {:else}
    <span class="toggle-dot light-active"></span>
    <span class="toggle-label">LIGHT</span>
  {/if}
</button>

<style>
  .theme-toggle {
    display: flex;
    align-items: center;
    gap: 6px;
    border: none;
    padding: 4px 10px;
    font-size: 11px;
    font-weight: 600;
    letter-spacing: 0.5px;
    color: var(--text-secondary);
  }

  .theme-toggle:hover {
    color: var(--text-primary);
    border: none;
  }

  .toggle-dot {
    width: 8px;
    height: 8px;
    border-radius: 50%;
  }

  .toggle-dot.dark-active {
    background: var(--text-primary);
  }

  .toggle-dot.light-active {
    background: var(--accent);
  }

  .toggle-label {
    font-size: 11px;
  }
</style>
