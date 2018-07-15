<template>
  <li>
    <div>
      <!-- period -->
      <span>
        {{ from }} - {{ to }}
      </span>

      <!-- title -->
      <span class="title">
        <slot></slot>
      </span>

      <!-- client w/o link -->
      <span v-if="link">
        <a :href="link" target="_blank">{{ client }}</a>
      </span>
      <span v-else>
        {{ client }}
      </span>

      <!-- +/- toggles -->
      <span class="right pointer" @click.prevent="toggle">
        <icon :name="icon"></icon>
      </span>

    </div>
  </li>
</template>

<script>
export default {
  name: 'CvEntry',
  props: {
    from: {
      type: String,
      required: true
    },
    to: {
      type: String,
      required: true
    },
    client: {
      type: String,
      required: true
    },
    link: {
      type: String,
      required: false
    }
  },
  data () {
    return {
      icon: 'plus-circle'
    }
  },
  methods: {
    toggle () {
      this.icon = (this.icon === 'plus-circle') ? 'minus-circle' : 'plus-circle'
    }
  }
}
</script>

<style scoped>
.title {
  font-weight: bolder;
  display: block;
}

.right {
  float: right;
}

.pointer {
  cursor: pointer;
}
</style>
