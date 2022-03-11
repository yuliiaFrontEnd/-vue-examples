<template>
  <picture v-if="imageData !== null">
    <source
      v-if="imageData.sm"
      :srcset="getUrl(imageData.sm.url)"
      :media="`(min-width: ${breakpoints.sm})`"
    />
    <source
      v-if="imageData.md"
      :srcset="getUrl(imageData.md.url)"
      :media="`(min-width: ${breakpoints.md})`"
    />
    <source
      v-if="imageData.lg"
      :srcset="getUrl(imageData.lg.url)"
      :media="`(min-width: ${breakpoints.lg})`"
    />
    <source
      v-if="imageData.xl"
      :srcset="getUrl(imageData.xl.url)"
      :media="`(min-width: ${breakpoints.xl})`"
    />
    <source
      v-if="imageData.xxl"
      :srcset="getUrl(imageData.xxl.url)"
      :media="`(min-width: ${breakpoints['2xl']})`"
    />
    <img
      :src="getUrl(getOriginal)"
      :class="{ 'w-full': fullWidth }"
      :alt="imageData.alt"
      loading="lazy"
    />
  </picture>
</template>

<script lang="ts">
import tailwindConfig from '~/tailwind.config'
import { I_Image } from '~/interface/Image'
import { PropType } from '@vue/composition-api'
import { ref } from '@nuxtjs/composition-api'

export default {
  name: 'atoms-image',
  props: {
    imageData: {
      type: Object as PropType<I_Image>,
      default: null,
    },
    fullWidth: {
      type: Boolean,
      default: false,
    },
  },
  setup() {
    const { screens: breakpoints } = tailwindConfig.theme
    const strapiUrl = ref(process.env.STRAPI_URL)

    return { breakpoints, strapiUrl }
  },
  computed: {
    getOriginal(): String {
      return (
        this.imageData?.original?.url ||
        this.imageData?.xxl?.url ||
        this.imageData?.xl?.url ||
        this.imageData?.lg?.url ||
        this.imageData?.md?.url ||
        this.imageData?.sm?.url
      )
    },
  },
  methods: {
    getUrl(base: String): String {
      return this.imageData?.isMock ? base : this.strapiUrl + base
    },
  },
}
</script>
