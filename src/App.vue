<template>
  <div id="app">
    <TheHeader></TheHeader>
    <transition mode="out-in">
      <router-view />
    </transition>
    <TheFooter></TheFooter>
  </div>
</template>

<script>
import TheHeader from "./components/TheHeader.vue";
import TheFooter from "./components/TheFooter.vue";
export default {
  components: {
    TheHeader,
    TheFooter,
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Poppins&display=swap");

* {
  box-sizing: border-box;
  background: #1c1c1c;
  font-family: "Poppins", sans-serif;
}

body,
ul,
li,
h1,
h2,
h3,
p {
  margin: 0;
  padding: 0;
}

ul {
  list-style: none;
}

#app {
  font-family: "Poppins", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: black;
}

.v-enter-active,
.v-leave-active {
  transition: opacity 0.3s;
}

.v-enter,
.v-leave-to {
  opacity: 0;
}
</style>
