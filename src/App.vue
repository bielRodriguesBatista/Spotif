<template>
  <div id="app">
    <header> 
    <h1>My music</h1>
    </header>
  <main>
    <section class="player">
      <h2 class="song"> {{current.title}} - <span> {{current.artist}} </span></h2>
      <div class="controls">
        <button class="prev">Prev</button>
        <button class="play" v-if="!isPlaying">Play</button>
        <button class="pause" v-else>Pause</button>
        <button class="next">Next</button>
      </div>
    </section>
  </main>
  </div>
</template>

<script>

export default {
  name: 'App',
  data(){
    return {
      current: {},
      index: 0,
      isPlaying: false,
      songs:  [
        {
          title: 'I fall apart',
          artist: 'Andrey Azizov Remix',
          src: require('./music/Post-Malone.mp3')
        },
        {
          title: 'Radioactive',
          artist: 'Imagine Dragons',
          src: require('./music/Imagine-Dragons-Radioactive.mp3')
        }
      ],
      player: new Audio()
    }
  },
    methods: {
      play(song){
        if(typeof song.src != 'undefined'){
          this.current = song;

          this.player.src = this.current.src;
        }

        this.player.play();
        this.isPlaying = true;
      }
    },
  created () {
    this.current = this.songs[this.index];
    this.player.src = this.current.src;
    // this.player.play();
  }

}
</script>

<style>
*{
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

body{
  font-family: sans-serif;
}

header{
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 15px;
  background-color: #212121;
  color: #fff;
}
</style>
