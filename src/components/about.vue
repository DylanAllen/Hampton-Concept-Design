<template>
  <div class="content">
    <section id="title">
      <div v-bind:style="{ left: titleShift + 'vw' }" class="first-title">
        <h1 id="first-text" v-bind:style="{ transform: 'translateX( -' + titleShift + 'vw)' }">ABOUT</h1>
      </div>
      <div class="second-title">
        <h1 id="second-text">ABOUT</h1>
      </div>

    </section>
    <section id="section2">
      <h2 v-bind:style="{ letterSpacing: titleShift/50 + 'vw' }">Lorem Ipsum</h2>
      <p>
        Hampton Creative is an advertising agency that takes itself moderately seriously. We mostly drink coffee and listen to music. Jesus, guns, and suburbs are our favorite. Snacks, soccer, America.
      </p>
      <p>
        Red everything. Brandon Grotesque whenever you can get away with it. Beaches vs. Mountains. Ping pong paddles, pants, and puns.
      </p>
    </section>
  </div>
</template>

<script>
export default {
  name: 'About',
  data () {
    return {
      scrollpos: 0,
      scrollfrac: 0,
      titleShift: 0
    }
  },
  watch: {
    scrollpos: function (val) {
      this.scrollfrac = val/(document.documentElement.offsetHeight - window.innerHeight)
      this.titleShift = (val / window.innerHeight) * 100
    }
  },
  methods: {
    handleScroll () {
      this.scrollpos = window.scrollY;
    }
  },
  beforeMount () {
  window.addEventListener('scroll', this.handleScroll);
  },
  beforeDestroy () {
    window.removeEventListener('scroll', this.handleScroll);
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
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
</style>
