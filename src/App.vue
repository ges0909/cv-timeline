<template>
  <div id="app">
    <CvTimeline :entries="entries" />
  </div>
</template>

<script>
import CvTimeline from '@/components/CvTimeline.vue'
import config from '@/config.js'

export default {
  name: 'app',
  data () {
    return {
      entries: config.entries
    }
  },
  components: {
    CvTimeline
  }
}
</script>

<style>
/* #app {
} */
</style>
