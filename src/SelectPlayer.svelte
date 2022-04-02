<script>
  export let open;
  export let player;
  function selectPlayer(e) {
    open = false;
    player = e;
  }
</script>

<dialog {open} class="dialog">
  <slot name="title">
    <h2 class="title">Tic Tac Toe</h2>
  </slot>
  <hr />
  <slot name="body" />
  <div class="btns">
    <slot name="btn">
      <button on:click={() => selectPlayer('X')} class="btn x">Player X</button>
      <button on:click={() => selectPlayer('O')} class="btn o">Player O</button>
    </slot>
  </div>
</dialog>

<style>
  .dialog {
    position: absolute;
    top: 30%;
    background-color: #bfd0e0;
    border: none;
    border-radius: 2rem;
  }
  hr {
    border: none;
    border-top: 2px solid var(--primary);
  }
  .title {
    text-align: center;
    color: var(--purple);
    font-style: italic;
    font-size: 4.5rem;
    margin: 0;
  }
  .text {
    font-style: oblique;
    color: var(--black);
  }
  .btns {
    display: flex;
    justify-content: center;
    margin-top: 10px;
  }
  .btn {
    background: none;
    border: none;
    cursor: pointer;
    font-size: 3.5rem;
    font-weight: 700;
    padding: 0.7rem;
  }
  .x,
  .o {
    border-radius: 1.7rem;
  }
  .x {
    margin-right: 15px;
    border: 3px solid #009ddc;
    color: var(--x);
  }
  .o {
    margin-left: 15px;
    border: 3px solid #f26430;
    color: var(--o);
  }
</style>
