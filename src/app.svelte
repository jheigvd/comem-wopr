<script>
  import Game from './game.svelte';
  import { currentGame } from './stores';

  const play = ai => () => currentGame.start(ai);
</script>

<style>
</style>

<header>
  <div class="navbar navbar-dark bg-dark shadow-sm">
    <div class="container d-flex justify-content-between">
      <a href="/" class="navbar-brand d-flex align-items-center">
        <strong> WOPR 🏆 ! </strong>
      </a>
    </div>
  </div>
</header>

<main>
  {#if !$currentGame}
    <section class="jumbotron text-center">
      <div class="container">
        <h1>Commence à jouer maintenant 👾 !</h1>
        <p class='mt-3'>
          <button type='button' class="btn btn-success btn-lg" on:click={play('random')}>Mode facile</button>
          <button type='button' class="btn btn-danger btn-lg" on:click={play('wopr')}>Joue à nouveau à WOPR !</button>
        </p>
      </div>
    </section>
  {/if}

  {#if $currentGame}
    <Game />
  {/if}

  {#if $currentGame && $currentGame.state !== 'playing'}
    <section class="text-center mt-4">
      <p>
        <button type='button' class="btn btn-success btn" on:click={play('random')}>Joue à nouveau en mode facile !</button>
        <button type='button' class="btn btn-danger btn" on:click={play('wopr')}>Joue à nouveau contre le WOPR !</button>
      </p>
    </section>
  {/if}
</main>