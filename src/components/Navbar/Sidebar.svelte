<script>
  import links from '../../constants/links'
  import { link } from 'svelte-routing'
  import globalStore from '../../stores/globalStore'
  import {fly, fade} from 'svelte/transition'
  import LoginLink from '../LoginLink.svelte'
</script>

<div class="sidebar-container" transition:fly={{x: -1000}}>
  <div class="sidebar" transition:fade={{delay: 400}}>
    <!-- header -->
    <div class="sidebar-header">
      <button
        class="btn-close"
        on:click={() => globalStore.toggleItem('sidebar', false)}
      >
        <i class="fas fa-window-close" />
      </button>
    </div>
    <!-- site logo -->
    <img src="/assets/images/logo.svg" alt="logo" class="logo sidebar-logo" />
    <!-- links -->
    <ul class="sidebar-links">
      {#each links as sidelink}
        <li>
          <a
            href={sidelink.url}
            use:link
            on:click={() => {
              globalStore.toggleItem('sidebar', false)
            }}>{sidelink.text}</a
          >
        </li>
      {/each}
      <li>
        <LoginLink />
      </li>
    </ul>
  </div>
</div>
