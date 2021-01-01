<template>
  <div id="nav">
    Copyright &#169; 2021
  </div>
  <router-view />
</template>

<style>
body {
  margin: 0 0;
  -webkit-touch-callout: none;
  -webkit-user-select: none;
  -khtml-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
  position: fixed;
  bottom: 0px;
  display: flex;
  flex: 1;
  justify-content: center;
  text-align: center;
  width: 100vw;
  font-size: 1.5rem;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
