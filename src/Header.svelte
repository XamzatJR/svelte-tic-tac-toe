<script>
  export let player;
</script>

<header class="details">
  <h1 class="title">Tic Tac Toe</h1>
  <div class="score">
    <div class="x">
      X <span>-</span>
    </div>
    <div class="o">
      O <span>-</span>
    </div>
  </div>
  <div class="turn">
    {player}'s turn
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
    border: 3px solid #009ddc;
    color: #009ddc;
  }
  .o {
    margin-left: 7.5rem;
    border: 3px solid #f26430;
    color: #f26430;
  }
</style>
