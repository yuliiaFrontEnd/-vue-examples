<template>
  <div :class="className">
    <div class="over-box">
      <promo-action-block
        :dark="isDark"
        :heading="heading"
        :button="button"
        :image="image"
        :staticContainer="staticContainer"
      >
        <template v-slot:abovebutton>
          <experience-list
            :light="isDark"
            v-if="experienceList.length > 0"
            :items="experienceList"
            :countGrid="experienceGrid"
          />
        </template>
      </promo-action-block>
    </div>

    <atoms-click-down v-if="clickDown" />
  </div>
</template>

<script lang="ts">
import { IHeadingTextProps } from '@/components/HeadingText.vue'
import { ButtonType } from '~/types/Base'
import { I_Image } from '~/interface/Image'
import { PropOptions } from 'vue'
import IExperienceList from '~/interface/ExperienceList'

export const strapiName = 'component.widget-with-image'

enum widgetWithIamgeType {
  grey = 'grey',
  navy = 'navy',
  hero = 'hero',
  transparent = 'transparent',
}

export default {
  name: 'widget-with-image',
  props: {
    heading: { type: Object as () => IHeadingTextProps },
    experienceList: <PropOptions<IExperienceList[]>>{
      type: Array,
      default: () => [],
    },
    experienceGrid: {
      type: Number,
      default: 3,
    },
    button: {
      type: Object as () => ButtonType,
      required: true,
    },
    image: {
      type: Object as () => I_Image,
      required: true,
    },
    type: {
      type: String as () => widgetWithIamgeType,
      default: widgetWithIamgeType.transparent,
    },
    staticContainer: {
      type: Boolean,
      default: false,
    },
    reverts: {
      type: Boolean,
      default: false,
    },
    clickDown: {
      type: Boolean,
      default: false,
    },
  },
  computed: {
    className() {
      return [
        'py-14',
        'md:py-32',
        {
          'reverts-content': this.reverts,
          ...this.checkClasses(),
        },
      ]
    },
    isDark() {
      return this.type === widgetWithIamgeType.navy
    },
  },
  methods: {
    checkClasses() {
      const classes = {}

      classes[widgetWithIamgeType[this.type] + '-widget'] = true

      return classes
    },
  },
  data() {
    return {}
  },
}
</script>

<style>
.reverts-content .intr-block {
  @apply lg:flex-row-reverse flex-col-reverse;
}
.reverts-content .img-block {
  @apply flex justify-end;
}
.hero-widget .img-block img {
  height: auto;
  max-width: none;
}
@media only screen and (max-width: calc(theme('screens.xl') - 1px)) {
  .reverts-content .static-container .info-block {
    @apply pl-6;
  }
}
@media only screen and (max-width: calc(theme('screens.lg') - 1px)) {
  .hero-widget .static-container .img-block {
    max-width: 1020px;
    @apply w-full px-0;
  }
  .hero-widget .img-block img {
    height: auto;
    max-width: 1000px;
  }
}
@media only screen and (max-width: calc(theme('screens.md') - 1px)) {
  .reverts-content .static-container .info-block {
    @apply px-4;
  }
}
@media only screen and (max-width: calc(theme('screens.sm') - 1px)) {
  .hero-widget .static-container .img-block {
    max-width: 760px;
    @apply w-full px-0;
  }
  .hero-widget .img-block img {
    height: auto;
    max-width: 580px;
  }
}
</style>

<style scoped>
.hero-widget,
.grey-widget {
  @apply bg-gray-100 w-full;
}
.grey-widget,
.navy-widget {
  @apply overflow-hidden w-full;
}
.navy-widget {
  background-color: theme('colors.navy.800');
  @apply relative;
}
.hero-widget {
  @apply relative pb-24 lg:py-0;
}
.navy-widget::before {
  content: '';
  background-image: url('/img/navy-ellipses.svg');
  background-repeat: no-repeat;
  background-position: 50% 50%;
  right: 50%;
  width: 994px;
  height: 994px;
  margin: -497px -794px 0 0;

  @apply absolute top-1/2 right-1/2;
}
.hero-widget .over-box::before {
  background-image: url('/img/circles.svg');
  background-repeat: no-repeat;
  background-position: 50% 50%;
  content: '';
  width: 77%;
  height: 100%;
  background-size: 994px 994px;
  margin: -380px 0 0 -240px;
  @apply absolute top-1/2 left-1/2;
}
.navy-widget.reverts-content::before {
  right: auto;
  left: 50%;
  margin: -497px 0 0 -750px;
}
.hero-widget .over-box {
  max-width: 100%;
  @apply overflow-hidden w-full relative pt-4 md:pt-20 lg:pt-28;
}
@media only screen and (max-width: calc(theme('screens.xl') - 1px)) {
  .hero-widget .over-box::before {
    width: 100%;
    margin: -380px 0 0 -250px;
  }
}
@media only screen and (max-width: calc(theme('screens.lg') - 1px)) {
  .navy-widget::before {
    margin: 0 -350px 0 0;
    width: 700px;
    height: 700px;
    background-size: 700px 700px;
    top: 0;
  }
  .hero-widget .over-box::before {
    background-size: 920px 920px;
    background-position: 50% -50%;
    margin: -580px 0 0 -460px;
    width: 920px;
    height: 920px;
  }
  .navy-widget.reverts-content::before {
    margin: 0 0 0 -350px;
  }
}
@media only screen and (max-width: calc(theme('screens.md') - 1px)) {
  .navy-widget::before {
    margin: 0 -250px 0 0;
    width: 500px;
    height: 500px;
    background-size: 500px 500px;
    top: 0;
  }
  .navy-widget.reverts-content::before {
    margin: 0 0 0 -250px;
  }
  .hero-widget .over-box::before {
    margin-top: -700px;
  }
}
@media only screen and (max-width: calc(theme('screens.sm') - 1px)) {
  .navy-widget {
    @apply overflow-hidden;
  }
  .navy-widget::before {
    margin: 0 -200px 0 0;
    width: 390px;
    height: 390px;
    background-size: 390px 390px;
    top: 0;
  }
  .navy-widget.reverts-content::before {
    margin: 0 0 0 -195px;
  }
  .hero-widget .over-box::before {
    background-size: 600px 600px;
    background-position: 50% -50%;
    margin: -380px 0 0 -300px;
    width: 600px;
    height: 600px;
  }
}
</style>
