<template>
  <li>
    <div>
      <!-- period -->
      <span>
        {{ from }} - {{ to }}
      </span>

      <span class="title">
        <slot />
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

      <slot name="task" show="false" />
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
  computed: {
  },
  methods: {
    toggle () {
      this.icon = (this.icon === 'plus-circle') ? 'minus-circle' : 'plus-circle'
    },
    isToggled () {
      return this.icon === 'minus-circle'
    }
  }
}
</script>

<style scoped>
.right {
  float: right;
}

.pointer {
  cursor: pointer;
}

.title {
  font-weight: bolder;
  display: block;
}
</style>
