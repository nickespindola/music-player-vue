<template>
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
</template>

<script>
export default {
  name: "PlaylistVue",
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
};
</script>

<style scoped>
h1 {
  font-size: 2.4rem;
  color: white;
  letter-spacing: 2px;
}

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