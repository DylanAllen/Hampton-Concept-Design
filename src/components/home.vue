<template>
  <div class="content">
    <section id="title">
      <div v-bind:style="{ left: titleShift + 'vw' }" class="first-title scroll" id="first-contain">
        <h1 class ="scroll" id="first-text" v-bind:style="{ transform: 'translateX( -' + titleShift + 'vw)' }">HAMPTON</h1>
      </div>
      <div class="second-title">
        <h1 id="second-text">HAMPTON</h1>
      </div>
    </section>
    <section id="section2">
      <h2 v-bind:style="{ letterSpacing: titleShift/300 + 'em' }">Lets Circle Up</h2>
      <p>
        Efficiently unleash cross-media information without cross-media value. Quickly maximize timely deliverables for real-time schemas. Dramatically maintain clicks-and-mortar solutions without functional solutions.
      </p>
      <p>
         Capitalize on low hanging fruit to identify a ballpark value added activity to beta test. Override the digital divide with additional clickthroughs from DevOps. Nanotechnology immersion along the information highway will close the loop on focusing solely on the bottom line.
      </p>
    </section>
    <section id="section3">
      <h2 v-bind:style="{ transform: 'translateX(' + ((Math.tan(random) * 100) - 50) + 'px) translateY(' + ((Math.tan(randomtwo) * 80) - 40) + 'px)' }" class="spinner">
        DISRUPTIVE
      </h2>
      <p class="backgrounded">
        Organically grow the holistic world view of disruptive innovation via workplace diversity and empowerment.
      </p>
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
      random: 0,
      randomtwo: 0,
      floater: 'bottom'
    }
  },
  watch: {
    scrollpos: function (val) {
      this.scrollfrac = val/(document.documentElement.offsetHeight - window.innerHeight)
      this.titleShift = Math.max((val / window.innerHeight) * 100, 0)
      this.random = Math.random()
      this.randomtwo = Math.random()
      if (this.scrollfrac > 0.5 && this.floater == 'bottom') {
        var floater = document.getElementById('floater')
        floater.classList.toggle('right')
        this.floater = 'right'
      } else if (this.scrollfrac < 0.5 && this.floater == 'right') {
        document.getElementById('floater').classList.toggle('right')
        this.floater = 'bottom'
      }
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
  },
  mounted () {
    var overscroll = function(el) {
      console.log(el)
      el.addEventListener('touchstart', function() {
        var top = el.scrollTop
          , totalScroll = el.scrollHeight
          , currentScroll = top + el.offsetHeight
        //If we're at the top or the bottom of the containers
        //scroll, push up or down one pixel.
        //
        //this prevents the scroll from "passing through" to
        //the body.
        if(top === 0) {
          el.scrollTop = 1
        } else if(currentScroll === totalScroll) {
          el.scrollTop = top - 1
        }
      })
      overscroll(document.getElementById('first-contain'))
      overscroll(document.getElementById('first-text'))
      el.addEventListener('touchmove', function(evt) {
        //if the content is actually scrollable, i.e. the content is long enough
        //that scrolling can occur
        if(el.offsetHeight < el.scrollHeight)
          evt._isScroller = true
      })
    }
    document.body.addEventListener('touchmove', function(evt) {
      //In this case, the default behavior is scrolling the body, which
      //would result in an overflow.  Since we don't want that, we preventDefault.
      if(!evt._isScroller) {
        evt.preventDefault()
      }
    })
  }
}
</script>

<style scoped>

</style>
