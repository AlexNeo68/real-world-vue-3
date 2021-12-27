<template>
  <div id="app">
    <div v-if="GStore.flashMessage">{{GStore.flashMessage}}</div>
    <div id="nav">
      <router-link :to="{name: 'EventList'}">Event List</router-link> |
      <router-link :to="{name: 'About'}">About</router-link>
    </div>
    <router-view />
  </div>
</template>

<script>
export default {
  inject: ['GStore'],
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}

h4 {
  font-size: 20px;
}

.navigation {
  display: flex;
  list-style: none;
  justify-content: center;
  column-gap: 25px;
  font-size: 18px;
}
.navigation a {
  color: rgb(23, 65, 88);
  text-decoration: none;
}

.navigation a.router-link-exact-active {
  border-bottom: 1px solid;
  font-weight: bold;
}
</style>
