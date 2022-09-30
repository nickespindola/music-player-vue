<template>
  <header>
    <nav>
      <div>
        <router-link to="/" class="logo">
          Nick's Playlist &#x1F3B5;
        </router-link>
        <router-link to="/about" class="btn"> About &#x1F3B6;</router-link>
      </div>
    </nav>
  </header>
</template>

<script>
export default {
  name: "TheHeader",
};
</script>

<style scoped>
nav {
  padding: 20px;
  border-bottom: 2px solid #404040;
  background: #111111;
}

nav a {
  font-size: 1.2rem;
  font-weight: bold;
  color: white;
  text-decoration: none;
  background: #111111;
}

nav a.router-link-exact-active {
  font-size: 2rem;
  transition: 0.3s;
  color: #5eead4;
}

nav a:hover {
  font-size: 2rem;
  transition: 0.3s;
  color: #5eead4;
}

div {
  width: 70%;
  margin: auto;
  display: flex;
  justify-items: center;
  justify-content: space-between;
  align-items: center;

  background: #111111;
}
</style>