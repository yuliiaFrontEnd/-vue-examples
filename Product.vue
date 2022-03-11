<template>
  <section :class="className">
    <div
      class="wrapper product flex flex-col md:flex-row items-center justify-between h-full"
    >
      <div
        v-scroller="'fadein-right'"
        class="image-block px-4 md:px-0 flex items-center relative mb-5 md:mb-0 col w-full md:w-1/2"
      >
        <div class="box bg-gray-100">
          <atoms-image v-if="imageData" :imageData="imageData" />
        </div>
      </div>
      <div class="text-block relative col w-full p-2 md:p-12 md:w-1/2">
        <div v-scroller.cascade="'fadein-left'" class="center-textbox bg-white">
          <slot></slot>
        </div>
      </div>
    </div>
  </section>
</template>

<script lang="ts">
import { PropType } from '@vue/composition-api'
import { I_Image } from '~/interface/Image'
export default {
  name: 'product',
  props: {
    right: { type: Boolean },
    imageData: {
      type: Object as PropType<I_Image>,
      default: null,
    },
  },
  data() {
    return {}
  },
  computed: {
    className() {
      return {
        'product-img': true,
        'pb-10': true,
        'md:pb-20': true,
        right: this.right,
      }
    },
  },
}
</script>

<style scoped>
.text-block .togg-boxing .title {
  @apply mb-6 px-2;
}
.product-img {
  @apply overflow-hidden w-full;
}
.wrapper {
  max-width: 1440px;
  @apply m-auto overflow-hidden md:overflow-visible;
}
.center-textbox {
  max-width: 430px;

  @apply m-auto;
}
.center-textbox .heading-text {
  @apply text-center md:text-left  p-0 mb-6;
}
.image-block .box {
  @apply rounded-3xl overflow-hidden;
}
.text-block {
  min-height: 100%;
}
.right .wrapper {
  @apply flex-row-reverse;
}
@media only screen and (max-width: calc(theme('screens.md') - 1px)) {
  .center-textbox {
    @apply text-center;
  }
  .center-textbox button {
    @apply mx-auto;
  }
  .right .wrapper {
    @apply flex-col;
  }
  .image-block .box,
  .right .image-block .box {
    border-radius: 12px;
  }
}
@media only screen and (max-width: calc(theme('screens.sm') - 1px)) {
  .wrapper {
    padding: 0 0.5rem;
  }
  .text-block {
    padding: 0.5rem 1rem;
  }
}
</style>
