<script>
  let board = ['', '', '', '', '', '', '', '', ''];
  $: winner = chooseWinner(board);
  export let player;
  function chooseWinner(boxes) {
    let winningStrategies = [
      [0, 1, 2],
      [3, 4, 5],
      [6, 7, 8],
      [0, 3, 6],
      [1, 4, 7],
      [2, 5, 8],
      [0, 4, 8],
      [2, 4, 6],
    ];

    for (let i = 0; i < winningStrategies.length; i++) {
      let [a, b, c] = winningStrategies[i];
      if (boxes[a] && boxes[a] === boxes[b] && boxes[a] === boxes[c]) {
        return boxes[a];
      }
    }
    return null;
  }
  function Clickers(i) {
    if (chooseWinner(board) || board[i]) {
      return;
    }
    board[i] = player;
    player = player === 'X' ? 'O' : 'X';
  }
</script>

<h2>{winner}</h2>
<main class="board">
  {#each board as box, id (id)}
    <div on:click={() => Clickers(id)} class="box">{box}</div>
  {/each}
</main>

<style>
  .board {
    display: grid;
    grid-template-columns: repeat(3, 166px);
    grid-template-rows: repeat(3, 166px);
    justify-items: center;
    margin: 5vh 0;
  }
  .box {
    width: 100%;
  }
  .box {
    border-right: 1rem solid #2a2d34;
    border-bottom: 1rem solid #2a2d34;
    display: flex;
    justify-content: center;
    align-items: center;
    cursor: pointer;
  }
  .box:nth-child(3n) {
    border-right: none;
  }
  .box:nth-child(7),
  .box:nth-child(8),
  .box:nth-child(9) {
    border-bottom: none;
  }
</style>
