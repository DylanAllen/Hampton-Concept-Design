<template>
  <div class="content">
    <section id="title">
      <div v-bind:style="{ left: titleShift + 'vw' }" class="first-title">
        <h1 id="first-text" v-bind:style="{ transform: 'translateX( -' + titleShift + 'vw)' }">HAMPTON</h1>
      </div>
      <div class="second-title">
        <h1 id="second-text">HAMPTON</h1>
      </div>
    </section>
    <section id="section2">
      <h2 v-bind:style="{ letterSpacing: titleShift/50 + 'vw' }">Expansive</h2>
      <p>
        Hampton Creative is an advertising agency that takes itself moderately seriously. We mostly drink coffee and listen to music. Jesus, guns, and suburbs are our favorite. Snacks, soccer, America.
      </p>
      <p>
        Red everything. Brandon Grotesque whenever you can get away with it. Beaches vs. Mountains. Ping pong paddles, pants, and puns.
      </p>
    </section>
    <section id="section3">
      <h2 v-bind:style="{ transform: 'translateX(' + (Math.cos(random) * 150 - 75) + 'px)' }" class="spinner">
        SHAKE IT UP
      </h2>
      <h3 class="red">
        You are not like everyone else. Let us help communicate who you are.
      </h3>
    </section>
    <div id="floater">
    </div>
  </div>
</template>

<script>
export default {
  name: 'Home',
  data () {
    return {
      scrollpos: 0,
      scrollfrac: 0,
      titleShift: 0,
      random: 0
    }
  },
  watch: {
    scrollpos: function (val) {
      this.scrollfrac = val/(document.documentElement.offsetHeight - window.innerHeight)
      this.titleShift = (val / window.innerHeight) * 100
      this.random = Math.random()
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

<style scoped>

</style>
