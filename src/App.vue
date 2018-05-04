<template>
  <div id="app">
    <nav>
      <router-link to="/">Home</router-link>
      <router-link to="/about">About</router-link>
    </nav>
    <router-view></router-view>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
import { mapMutations } from 'vuex'

export default {
  name: 'app',
  data () {
    return {

    }
  },
  computed: {
    ...mapGetters([
      'safelyStoredNumber'
    ])
  },
  methods: {
    ...mapMutations([
      'incrementStoredNumber',
      'setStoredNumber'
    ])
  }
}
</script>

<style>
body {
  margin: 0;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

nav {
    position: fixed;
    top: 5px;
    right: 5px;
    z-index:1000;
}

nav a {
    padding: 12px;
    font-size: 20px;
    text-decoration: none;
    color: red;
}

h1 {
  color: red;
  position: absolute;
  background-color: #ffffff;
  font-size: 18vw;
}

#section2 h2 {
    padding-top: 20vh;
    font-size: 6vw;
    text-align: center;
}

section {
  height: 100vh;
  position: relative;
}

section#section2 {
  z-index: 30;
  background-color: rgba(100,0,0,0.8);
  color: #ffffff
}

#section3 {
  background-color: rgba(255,255,255,0.8);
  z-index: 40;
}

h2.spinner {
  padding-top: 20vh;
  color: red;
  font-size:10vw;
  transition: all 0.1s linear;
}

h1.first-title {
  z-index:20;
}
h1.second-title {
  z-index:10;
}
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

p {
  max-width: 800px;
  padding: 20px;
  margin: auto;
  font-size:20px;
  text-align:left;
}
.reveal .first-title h1 {
    transform: translateX(-300px);
}

.reveal .first-title {
  left: 300px;
}

.title-holder {
    position: fixed;
    overflow: hidden;
}

.first-title {
    position: fixed;
    overflow: hidden;
    z-index: 20;
    height: 110vh;
    width: 100vw;
    background-color: #ffffff;
}

.second-title {
    position: fixed;
    overflow: hidden;
    z-index: 10;
    height: 110vh;
    width: 100vw;
}
h1#second-text {
    color: #ffffff!important;
    background-color: red;
}

#floater {
  position: fixed;
  transition: all 0.2s ease-out;
  height: 5vh;
  width: 100vw;
  background-color: red;
  bottom: 0;
  left: 0;
  right: 0;
}

#floater.left {
  height: 100vh;
  width: 5vw;
  top: 0;
  left: 0;
  right: auto;
  bottom: 0;
}
</style>
