<template>
  <div :class="className">
    <div
      class="flex mb-2 mr-0 md:mr-4"
      v-for="(item, index) in items"
      :key="index"
    >
      <div class="img flex items-center mr-2 mx-3 md:ml-0">
        <atoms-image :imageData="getIcon(item.icon)" />
      </div>
      <p>{{ item.content }}</p>
    </div>
  </div>
</template>

<script lang="ts">
import { PropOptions } from 'vue'
import IExperianceList from '~/interface/ExperienceList'
import tailwindConfig from '~/tailwind.config'

export default {
  name: 'experience-list',
  props: {
    light: { type: Boolean },
    items: <PropOptions<IExperianceList[]>>{
      type: Array,
      required: true,
    },
    countGrid: {
      type: Number,
      default: 3,
    },
  },
  mounted() {
    window.addEventListener('resize', this.checkIsMobile)
    this.checkIsMobile()
  },
  computed: {
    className() {
      return [
        'pb-6',
        'md:pb-8',
        'grid',
        'experience-list',
        {
          light: this.light,
          'grid-cols-2': this.isMobile,
          [`grid-cols-${this.countGrid}`]: !this.isMobile,
        },
      ]
    },
  },
  methods: {
    getIcon(icon) {
      return { original: { url: icon.url } }
    },
    checkIsMobile() {
      this.isMobile =
        document?.defaultView?.innerWidth <=
        parseInt(tailwindConfig?.theme?.screens?.md)
    },
  },
  data() {
    return {
      isMobile: false,
    }
  },
}
</script>
<style scoped>
.experience-list.light p {
  color: white;
}
.grid-cols-3,
.grid-cols-2 {
  max-width: 100%;
}
.img {
  min-width: 18px;
  max-width: 18px;
  min-height: 16px;
  height: 16px;
  margin-top: 0.35rem;
}
@media only screen and (max-width: calc(theme('screens.md') - 1px)) {
  .grid-cols-3 {
    width: 280px;
  }
}
</style>
