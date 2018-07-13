<template>
  <section class="timeline">
    <ul>
      <li v-for="item of entries" :key="item.id">
        <div>
          <span class="when">{{ item.from }} - {{ item.to }}</span>

          <span class="what">{{ item.title }}</span>

          <span class="where" v-if="item.link">
            <a :href="item.link" target="_blank">{{ item.company }}</a>
          </span>

          <span class="where" v-else>
            {{ item.company }}
          </span>

          <span class="toggle">
            <icon name="plus-circle"></icon>
            <icon name="minus-circle"></icon>
          </span>

        </div>
      </li>
    </ul>
  </section>
</template>

<script>
export default {
  name: 'CvTimeline',
  props: {
    entries: {
      type: Array,
      required: true
    }
  },
  data () {
    return {
      icon: 'coffee'
    }
  },
  methods: {
    isElementInViewport (el) {
      var rect = el.getBoundingClientRect()
      return (
        rect.top >= 0 &&
        rect.left >= 0 &&
        rect.bottom <= (window.innerHeight || document.documentElement.clientHeight) &&
        rect.right <= (window.innerWidth || document.documentElement.clientWidth)
      )
    },
    callbackFunc () {
      let self = this
      document.querySelectorAll('.timeline li').forEach(div => {
        if (self.isElementInViewport(div)) {
          div.classList.add('in-view')
        }
      })
    }
  },
  mounted () {
    this.entries.forEach(function (entry, index) { entry['id'] = index })
    window.addEventListener('load', this.callbackFunc)
    window.addEventListener('resize', this.callbackFunc)
    window.addEventListener('scroll', this.callbackFunc)
  }
}
</script>

<style scoped>
*,
*::before,
*::after {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  font: normal 16px/1.5 "Helvetica Neue", sans-serif;
  background: #456990;
  color: #fff;
  overflow-x: hidden;
  padding-bottom: 50px;
}

/* INTRO SECTION
–––––––––––––––––––––––––––––––––––––––––––––––––– */

.intro {
  background: #f45b69;
  padding: 100px 0;
}

.container {
  width: 90%;
  max-width: 1200px;
  margin: 0 auto;
  text-align: center;
}

h1 {
  font-size: 2.5rem;
}

/* TIMELINE
–––––––––––––––––––––––––––––––––––––––––––––––––– */

.timeline ul {
  background: #456990;
  padding: 50px 0;
}

.timeline ul li {
  list-style-type: none;
  position: relative;
  width: 6px;
  margin: 0 auto;
  padding-top: 50px;
  background: #fff;
}

.timeline ul li::after {
  content: "";
  position: absolute;
  left: 50%;
  bottom: 0;
  transform: translateX(-50%);
  width: 30px;
  height: 30px;
  border-radius: 50%;
  background: inherit;
}

.timeline ul li div {
  position: relative;
  bottom: 0;
  width: 400px;
  padding: 15px;
  background: #f45b69;
}

.timeline ul li div::before {
  content: "";
  position: absolute;
  bottom: 7px;
  width: 0;
  height: 0;
  border-style: solid;
}

.timeline ul li:nth-child(odd) div {
  left: 45px;
}

.timeline ul li:nth-child(odd) div::before {
  left: -15px;
  border-width: 8px 16px 8px 0;
  border-color: transparent #f45b69 transparent transparent;
}

.timeline ul li:nth-child(even) div {
  left: -439px;
}

.timeline ul li:nth-child(even) div::before {
  right: -15px;
  border-width: 8px 0 8px 16px;
  border-color: transparent transparent transparent #f45b69;
}

time {
  display: block;
  font-size: 1.2rem;
  font-weight: bold;
  margin-bottom: 8px;
}

/* EFFECTS
–––––––––––––––––––––––––––––––––––––––––––––––––– */

.timeline ul li::after {
  transition: background 0.5s ease-in-out;
}

.timeline ul li.in-view::after {
  background: #f45b69;
}

.timeline ul li div {
  visibility: hidden;
  opacity: 0;
  transition: all 0.5s ease-in-out;
}

.timeline ul li:nth-child(odd) div {
  transform: translate3d(200px, 0, 0);
}

.timeline ul li:nth-child(even) div {
  transform: translate3d(-200px, 0, 0);
}

.timeline ul li.in-view div {
  transform: none;
  visibility: visible;
  opacity: 1;
}

/* GENERAL MEDIA QUERIES
–––––––––––––––––––––––––––––––––––––––––––––––––– */

@media screen and (max-width: 900px) {
  .timeline ul li div {
    width: 250px;
  }
  .timeline ul li:nth-child(even) div {
    left: -289px;
    /*250+45-6*/
  }
}

@media screen and (max-width: 600px) {
  .timeline ul li {
    margin-left: 20px;
  }
  .timeline ul li div {
    width: calc(100vw - 91px);
  }
  .timeline ul li:nth-child(even) div {
    left: 45px;
  }
  .timeline ul li:nth-child(even) div::before {
    left: -15px;
    border-width: 8px 16px 8px 0;
    border-color: transparent #f45b69 transparent transparent;
  }
}

.what {
  font-weight: bolder;
  display: block;
}

.toggle {
  float: right;
}
</style>
