<script>
  import SelectPlayer from './SelectPlayer.svelte';
  import { ocount, xcount } from './store';
  export let player;
  let board = [null, null, null, null, null, null, null, null, null];
  $: winner = chooseWinner(board);
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
        if (boxes[a] === 'X') {
          xcount.update((n) => n + 1);
        } else if (boxes[a] === 'O') {
          ocount.update((n) => n + 1);
        }
        return boxes[a];
      } else if (board.every((el) => el !== null)) {
        return 'Match has been drawn';
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
  function playAgain() {
    board = [null, null, null, null, null, null, null, null, null];
  }
</script>

<SelectPlayer bind:open={winner}>
  <h2 slot="title" class="title">
    {winner !== 'Match has been drawn' ? `${winner} win` : winner}
  </h2>
  <button class="btn" slot="btn" on:click={playAgain}>Play again!</button>
</SelectPlayer>

<main class="board">
  {#each board as box, id (id)}
    <div
      on:click={() => Clickers(id)}
      class="box"
      style:color={box === 'X' ? '#009ddc' : '#f26430'}
    >
      {box ? box : ''}
    </div>
  {/each}
</main>

<style>
  .board {
    display: grid;
    grid-template-columns: repeat(3, calc(var(--index) + 138px));
    grid-template-rows: repeat(3, calc(var(--index) + 138px));
    justify-items: center;
    margin: 5vh 0;
  }
  .box {
    width: 100%;
    font-size: 15rem;
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
  .btn {
    border: 4px solid var(--x);
    border-radius: 1rem;
    padding: 2px 10px;
    font-size: 2.4rem;
    font-weight: 600;
    background-color: var(--primary);
    color: var(--x);
  }
</style>
