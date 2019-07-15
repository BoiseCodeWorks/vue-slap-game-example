<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
    <h1>stuff</h1>
    <!-- <router-view /> -->
    <Home :target="target" />
    <Home :target="target2" />
  </div>
</template>

<script>
  import Home from './views/Home.vue'
  export default {
    data() {
      return {
        target: {
          name: "Battleship",
          health: 100,
          hits: 0,
          attacks: [
            {
              name: "Slap",
              dmg: -1
            },
            {
              name: "Torpedo",
              dmg: 10
            },
            {
              name: "Nuke",
              dmg: 1000000
            }
          ]
        },
        target2: {
          name: "Batman",
          health: 500,
          hits: 0,
          attacks: [
            {
              name: "Batarang",
              dmg: -20
            },
            {
              name: "Kick",
              dmg: 10
            },
            {
              name: "Weakness",
              dmg: 0
            }
          ]
        }
      }
    },
    components: {
      Home
    }
  }
</script>

<style>
  h1 {
    color: orangered;
  }

  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
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
</style>