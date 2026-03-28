<script lang="ts">
  import { activeTab, tabs, type TabId } from "../../lib/store";
  import ThemeToggle from "./ThemeToggle.svelte";

  function setTab(id: TabId) {
    activeTab.set(id);
  }
</script>

<nav class="topbar">
  <div class="topbar-tabs">
    {#each tabs as tab}
      <button
        class="tab-btn"
        class:active={$activeTab === tab.id}
        on:click={() => setTab(tab.id)}
      >
        {tab.label}
      </button>
    {/each}
  </div>
  <div class="topbar-right">
    <ThemeToggle />
  </div>
</nav>

<style>
  .topbar {
    display: flex;
    align-items: center;
    justify-content: space-between;
    height: 36px;
    border-bottom: 1px solid var(--border);
    background: var(--surface);
    padding: 0 4px;
    flex-shrink: 0;
  }

  .topbar-tabs {
    display: flex;
    align-items: center;
    gap: 0;
    overflow-x: auto;
  }

  .tab-btn {
    border: none;
    padding: 8px 14px;
    font-size: 12px;
    font-weight: 500;
    color: var(--text-secondary);
    background: none;
    white-space: nowrap;
    height: 36px;
    position: relative;
  }

  .tab-btn:hover {
    color: var(--text-primary);
    border: none;
  }

  .tab-btn.active {
    color: var(--text-primary);
    border: none;
  }

  .tab-btn.active::after {
    content: "";
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    height: 1px;
    background: var(--accent);
  }

  .topbar-right {
    display: flex;
    align-items: center;
    flex-shrink: 0;
  }
</style>
