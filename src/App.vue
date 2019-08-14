<template>
  <div id="app" class="container">
    <div id="nav">
      <router-link to="/" class="nav-item">Home</router-link>|
      <router-link to="/about" class="nav-item">About</router-link>
    </div>
    <router-view />
  </div>
</template>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  align-items: center;
  display: flex;
  flex-direction: column;
  justify-content: center;
  height: 900px;
}
#nav {
  background: #2c3e50;
  width: 100%;
  display: flex;
}
.nav-item {
  color: wheat;
  padding: 20px;
  font-size: 20px;
  font-weight: 900;
  text-decoration: none;
}

@import "./assets/style.css";
</style>
