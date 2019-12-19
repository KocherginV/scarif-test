<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
    <router-view/>
    <div>
      <hr>
        <p>Is highframe active: </p> {{highFrameActive}}
    </div>
  </div>
</template>

<script>
import { HighframeChild } from 'highframe'

const parentOrigins = [
  'http://localhost:8080',
  'https://staging-dashboard.tillhub.com',
  'https://dashboard.tillhub.com'
]

export default {
  data () {
    return {
      parent: null,
      highFrameActive: false
    }
  },

  mounted () {
    const self = this
    this.parent = new HighframeChild({ parentOrigins })
    this.parent.on('model', (model) => {
      self.highFrameActive = true
    })
  }
}

</script>

<style>
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
