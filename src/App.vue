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
        <div class="control">
          <button>Prev</button>
          <button v-if="!isPlaying" @click="play">Play</button>
          <button v-else @click="pause">Pause</button>
          <button>Next</button>
        </div>
      </section>
      <section class="playlist">
        <h3>The Playlist</h3>
        <button v-for="song in songs" :key="song.src" @click="play(song)" :class="(song.src == current.src) ? 'song playing' : 'song' "></button>
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
      isPlaying: false,
      songs: [
      {
        title: 'Spectre',
        artist: 'Alan Walker',
        src: require('./assets/alan-walker-spectre.mp3')
      },
      {
        title: 'Faded',
        artist: 'Alan Walker',
        src: require('./assets/alan-walker-fade.mp3')
      }
      ],
      player: new Audio()
    }
  },
  methods: {
    play(song) {
      if (typeof song.src != "undefined") {
        this.current = song;

        this.player.src = this.current.src;
      }

      this.player.play();
      this.isPlaying = true;
    },
    pause () {
      this.player.pause();
      this.isPlaying = false;
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
