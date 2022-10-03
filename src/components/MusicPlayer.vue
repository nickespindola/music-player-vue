<template>
  <section>
    <div class="content">
      <div class="text">
        <h3>Currently Playing:</h3>
        <h1>{{ current.title }}</h1>
        <h2>{{ current.artist }}</h2>
      </div>
      <div class="container">
        <img :src="current.album" />
      </div>
      <div class="player">
        <button class="btn prev" @click="prev">PREV</button>
        <div :class="[isPlaying ? 'pause' : 'play']" @click="togglePlay"></div>
        <button class="btn next" @click="next">NEXT</button>
      </div>
    </div>
    <div class="playlist">
      <h1>Playlist:</h1>
      <button
        class="playlist-btn"
        v-for="song in songs"
        :key="song.src"
        @click="play(song)"
        :class="song.src == current.src ? 'song playing' : 'song'"
      >
        {{ song.title }} - {{ song.artist }}
      </button>
    </div>
    <!-- <Playlist></Playlist> -->
  </section>
</template>

<script>
// import Playlist from "./Playlist.vue";

export default {
  name: "MusicPlayer",
  props: {
    msg: String,
  },
  data() {
    return {
      current: {},
      index: 0,
      isPlaying: false,
      songs: [
        {
          title: "Got the Life",
          artist: "Korn",
          album: require("../assets/follow-the-leader.jpg"),
          src: require("../assets/onlymp3.to - Korn- Got the Life-emNahB_96JY-192k-1654558455048.mp3"),
        },
        {
          title: "Nookie",
          artist: "Limp Bizkit",
          album: require("../assets/significant-other.png"),
          src: require("../assets/onlymp3.to - Limp Bizkit - Nookie (Official Music Video)-JTMVOzPPtiw-192k-1654559891785.mp3"),
        },
        {
          title: "The Only",
          artist: "Shadow Zone",
          album: require("../assets/shadow-zone.png"),
          src: require("../assets/onlymp3.to - Static-X - The Only (Official Music Video)  Warner Vault-vMCbJB4yNXo-192k-1654560066385.mp3"),
        },
        {
          title: "Be Quiet And Drive",
          artist: "Deftones",
          album: require("../assets/around-the-fur.jpg"),
          src: require("../assets/onlymp3.to - Deftones - Be Quiet And Drive (Far Away) (Official Music Video)  Warner Vault-KvknOXGPzCQ-192k-1654566820974.mp3"),
        },
      ],
      player: new Audio(),
    };
  },
  methods: {
    togglePlay() {
      let method = this.isPlaying ? "pause" : "play";
      this.player[method]();
      this.isPlaying = !this.isPlaying;
    },
    play(song) {
      if (typeof song.src != "undefined") {
        this.current = song;
        this.player.src = this.current.src;
      }
      this.player.play();
      this.player.addEventListener(
        "ended",
        function () {
          this.index++;

          if (this.index > this.songs.length - 1) {
            this.index = 0;
          }
          this.current = this.songs[this.index];
          this.play(this.current);
        }.bind(this)
      );
      this.isPlaying = true;
    },
    next() {
      this.index++;
      if (this.index > this.songs.length - 1) {
        this.index = 0;
      }
      this.current = this.songs[this.index];
      this.play(this.current);
    },
    prev() {
      this.index--;
      if (this.index < 0) {
        this.index = this.songs.length - 1;
      }
      this.current = this.songs[this.index];
      this.play(this.current);
    },
  },
  created() {
    this.current = this.songs[this.index];
    this.player.src = this.current.src;
  },
  // components: { Playlist },
};
</script>

<style scoped>
section {
  display: flex;
  flex-direction: row;
  height: 740px;
  width: 60%;
  margin: auto;
  margin-top: 20px;
}

h3 {
  font-size: 1rem;
  color: #14b8a6;
  letter-spacing: 2px;
}
h1 {
  font-size: 2.4rem;
  color: white;
  letter-spacing: 2px;
}
h2 {
  font-size: 1.7rem;
  color: #14b8a6;
  letter-spacing: 1px;
}

.content {
  display: flex;
  flex-direction: column;
  height: 720px;
  width: 650px;
  justify-content: space-around;
}

.text {
  display: flex;
  flex-direction: column;
  height: 120px;
  justify-content: space-between;
}

.container {
  margin: auto;
  width: 450px;
  height: 45s0px;
}

img {
  width: 450px;
  height: 450px;
  border-radius: 30px;
}

.player {
  display: flex;
  margin: auto;
  align-items: center;
  width: 380px;
  justify-content: space-around;
}

/* PLAY/PAUSE BUTTON */
.play {
  box-sizing: border-box;
  width: 0;
  height: 74px;
  border-style: solid;
  border-width: 37px 0 37px 60px;
  border-color: transparent transparent transparent #14b8a6;
  cursor: pointer;
  will-change: border-width;
  transition: all 0.2s ease;
}
.pause {
  box-sizing: border-box;
  width: 0;
  height: 74px;
  border-style: double;
  border-width: 0px 0 0px 60px;
  border-color: transparent transparent transparent #14b8a6;
  cursor: pointer;
  will-change: border-width;
  transition: all 0.2s ease;
}

.play:hover {
  border-color: transparent transparent transparent #5eead4;
}
.pause:hover {
  border-color: transparent transparent transparent #5eead4;
}

/* PREVIOUS / NEXT BUTTON */
.btn {
  font-size: 1.5rem;
  border: none;
  color: #b6b6b8;
  cursor: pointer;
  transition: 0.2s;
  letter-spacing: 1px;
}

.btn:hover {
  color: white;
  transition: 0.2s;
}

/* PLAYLIST */
.playlist {
  display: flex;
  flex-direction: column;
  /* border: 2px solid black; */
  padding: 10px;
  border-radius: 5px;
  /* height: 500px;
  justify-content: space-around; */
}

.playlist-btn {
  font-size: 1.2rem;
  padding: 10px;
  width: 400px;
  height: 50px;
  margin-top: 15px;

  border: 2px solid #14b8a6;
  border-radius: 15px;

  background-color: #14b8a6;

  cursor: pointer;
  transition: 0.2s;

  font-weight: bold;

  background: linear-gradient(#14b8a6 0 0) var(--p, 0) / var(--p, 0) no-repeat;
  transition: 0.3s, background-position 0s;

  color: #b6b6b8;
  letter-spacing: 1px;
}

.playlist-btn:hover {
  --p: 100%;
  color: white;
  letter-spacing: 1px;
}
</style>