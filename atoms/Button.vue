<template>
  <button :class="className" @click="btnClick">
    <slot></slot>
  </button>
</template>
<script lang="ts">
import { PropType, PropOptions } from 'vue'
import { btnCallback } from '@/types/ButtonCallbackType'

export enum btnSize {
  middle = 'middle',
  large = 'large',
  small = 'small',
}

export enum btnColor {
  blue = 'blue',
  black = 'black',
  white = 'white',
  navy = 'navy',
  transparent = 'transparent',
}

enum btnColorClasses {
  blue = 'bg-blue',
  black = 'bg-black',
  white = 'bg-white',
  navy = 'bg-navy-0.3',
  transparent = 'transparent',
}

enum btnSizeClasses {
  middle = 'middleHeight',
  large = 'largeHeight',
  small = 'smallHeight',
}

enum btnTextColor {
  black = 'text-black',
  white = 'text-white',
}

enum btnBorder {
  gray = 'border border-solid border-gray-300 leading-5',
  navy = 'border border-solid border-white border-opacity-25',
}

export interface IButtonProps {
  size: PropOptions<btnSize>
  color: PropOptions<btnColor>
  callback: PropOptions<btnCallback>
  href: PropOptions<String>
  rounded: PropOptions<Boolean>
  external: PropOptions<Boolean>
  url: PropOptions<Object>
}

export const props: IButtonProps = {
  color: {
    type: String as () => btnColor,
    default: btnColor.blue,
  },
  size: {
    type: String as () => btnSize,
    default: btnSize.middle,
  },
  callback: {
    type: Object as PropType<btnCallback>,
  },
  href: {
    type: String,
    default: null,
  },
  rounded: {
    type: Boolean,
    default: true,
  },
  external: {
    type: Boolean,
    default: false,
  },
  url: {
    type: Object,
    default: () => {},
  },
}

export default {
  name: 'Button',
  props,
  computed: {
    className() {
      return {
        btn: true,
        'py-3': true,
        'rounded-lg': this.rounded,
        ...this.checkClasses(),
      }
    },
  },
  methods: {
    checkClasses() {
      const classes = {}

      classes[btnColorClasses[this.color]] = true

      if (
        this.color === btnColor.white ||
        this.color === btnColor.transparent
      ) {
        classes[btnTextColor.black] = true
      } else {
        classes[btnTextColor.white] = true
      }

      if (this.color === btnColor.navy) {
        classes[btnBorder.navy] = true
      } else if (this.color === btnColor.transparent) {
        classes[btnBorder.gray] = true
      }

      classes[btnSizeClasses[this.size]] = true

      return classes
    },
    btnClick() {
      this.callback?.before?.()

      if (!this.external) {
        if (this.url && this.url.url) {
          this.$router.push(this.url.url)
        }
      } else {
        window.location.host = this.href
      }

      this.callback?.after?.()
    },
  },
}
</script>

<style scoped>
.btn {
  @apply font-biennale font-medium tracking-widest flex items-center text-tiny;

  transition: all 0.5s;
  text-transform: uppercase;
  padding-left: 1.5rem;
  padding-right: 1.5rem;
  font-weight: 600;
  line-height: 14px;
}
.btn:hover {
  opacity: 0.7;
}
.middleHeight {
  height: 3rem;
}
.largeHeight {
  height: 3.5rem;
}
.smallHeight {
  height: 2.5rem;
  padding: 0.8rem 1rem;
  width: 5.56rem;
}

@media only screen and (max-width: calc(theme('screens.md') - 1px)) {
  .btn {
    padding-left: 1.2rem;
    padding-right: 1.2rem;
    font-size: 0.75rem;
  }
  .middleHeight,
  .largeHeight {
    height: 3rem;
  }
  .smallHeight {
    height: 2.3rem;
    padding: 0.6rem 0.85rem;
  }
}
</style>
