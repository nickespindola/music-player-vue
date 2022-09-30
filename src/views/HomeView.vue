<template>
  <div class="home">
    <MusicPlayer />
  </div>
</template>

<script>
// @ is an alias to /src
import MusicPlayer from "@/components/MusicPlayer.vue";

export default {
  name: "HomeView",
  components: {
    MusicPlayer,
  },
};
</script>
