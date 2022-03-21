<script>
  import Header from './Header.svelte';
  import Main from './Main.svelte';
  import SelectPlayer from './SelectPlayer.svelte';
  let open = true;
  let player;
  // --black: #2A2D34;
  // --purple: #6761A8;
  // --green: #009B72;
</script>

<div class="play-board">
  <SelectPlayer bind:player {open} />
  <Header bind:player />
  <Main bind:player />
</div>
