<script>
  import Header from './Header.svelte';
  import Main from './Main.svelte';
  import SelectPlayer from './SelectPlayer.svelte';

  let open = true;
  let player;
</script>

<div class="play-board">
  <SelectPlayer bind:player {open}>
    <div slot="body" class="text">Select which one you want to be?</div>
  </SelectPlayer>
  <Header bind:player />
  <Main bind:player />
</div>

<style>
  .play-board {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
</style>
