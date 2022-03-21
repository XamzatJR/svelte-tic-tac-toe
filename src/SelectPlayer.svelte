<script>
  export let open;
  export let player;
  function selectPlayer(e) {
    open = false;
    player = e;
  }
</script>

<dialog {open} class="dialog">
  <h3 class="title">Tic Tac Toe</h3>
  <hr />
  <div class="text">Select which one you want to be?</div>
  <div class="btns">
    <button on:click={() => selectPlayer('X')} class="btn">X</button>
    <button on:click={() => selectPlayer('O')} class="btn">O</button>
  </div>
</dialog>

<style>
  .dialog {
  }
  .title {
  }
  .text {
  }
  .btn {
  }
</style>
