<script>
  import { xcount, ocount } from './store';
  export let player;
</script>

<header class="details">
  <h1 class="title">Tic Tac Toe</h1>
  <div class="score">
    <div class="x">
      X <span>{$xcount === 0 ? '-' : $xcount}</span>
    </div>
    <div class="o">
      O <span>{$ocount === 0 ? '-' : $ocount}</span>
    </div>
  </div>
  <div class="turn">
    {player ? player : 'Boom'}'s turn
  </div>
</header>

<style>
  .title {
    font-size: 7rem;
    margin: 2vh auto 4vh;
    color: #6761a8;
    font-style: oblique;
  }
  .details {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 1280px;
  }
  .score {
    display: flex;
  }
  .x,
  .o {
    border-radius: 1.7rem;
    width: 15rem;
    font-size: 3.5rem;
    font-weight: 700;
    display: flex;
    justify-content: space-around;
  }
  .x {
    margin-right: 7.5rem;
    border: 3px solid var(--x);
    color: var(--x);
  }
  .o {
    margin-left: 7.5rem;
    border: 3px solid var(--o);
    color: var(--o);
  }
  .turn {
    margin-top: 20px;
  }
</style>
