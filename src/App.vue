<template>
  <div id="app">
    <header>
      My Music
    </header>
    <main>
      <section class="player">
        <h2 class="song-title">
          {{  current.title }} - <span>{{ current.artist}}</span>
        </h2>
      </section>
    </main>
  </div>
</template>

<script>


export default {
  name: 'App',
  data() {
    return {
      current: {},
      index: 0,
      songs: [
      {
        title: 'Spectre',
        artist: 'Alan Walker',
        src: require('./assets/alan-walker-spectre.mp3')
      },
      {
        title: 'Faded',
        artist: 'Alan Walker',
        src: require('./assets/alan-walker-spectre.mp3')
      }
      ],
      player: new Audio()
    }
  },
  created() {
    this.current = this.songs[this.index];
    this.player.src = this.current.src;
    //this.player.play();
  }
}
</script>

<style>

</style>
