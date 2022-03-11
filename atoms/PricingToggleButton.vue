<template>
  <div class="pricing-toggle flex justify-center items-center mb-8 relative">
    <div class="togg-bx w-56 flex justify-between items-center pr-4">
      <span :class="!currentState ? 'active' : ''" v-if="value.length > 0">{{
        value[0].data
      }}</span>
      <label :class="className">
        <input
          type="checkbox"
          :name="name"
          :checked="checked"
          @change="toggle"
        />
        <div class="v-toggle_thumb" :style="position" />
      </label>
      <span :class="currentState ? 'active' : ''" v-if="value.length > 1">{{
        value[1].data
      }}</span>
    </div>
    <span class="sub-info">{{ tag }}</span>
  </div>
</template>

<script lang="ts">
import { PropOptions } from 'vue'

export interface IPricingToggleValues {
  data: String
}

export interface IPricingToggle {
  checked: Boolean
  name: String
  value: IPricingToggleValues[]
  tag: String
}

interface IPricingToggleProps {
  checked: PropOptions<Boolean>
  name: PropOptions<String>
  value: PropOptions<IPricingToggleValues[]>
  tag: PropOptions<String>
}

const props: IPricingToggleProps = {
  checked: {
    type: Boolean,
    default: false,
  },
  name: { type: String },
  value: {
    type: Array,
    default: () => [],
  },
  tag: { type: String },
}

export default {
  name: 'pricing-toggle',
  props,
  computed: {
    className() {
      return {
        'v-toggle': true,
        active: this.currentState,
      }
    },
    position() {
      return {
        left: (this.currentState ? 38 : 6) + 'px',
      }
    },
  },
  methods: {
    toggle(event) {
      this.currentState = event.target.checked
      const _state =
        this.value.length > 1
          ? this.value[~~this.currentState]
          : this.currentState

      this.$emit('change', _state)
    },
  },
  data() {
    return {
      currentState: this.checked,
    }
  },
}
</script>

<style scoped>
.v-toggle {
  transition: all 0.3s;
  height: 40px;
  width: 74px;
  @apply border border-solid border-gray-300 rounded-3xl cursor-pointer relative p-2;
}
.v-toggle.disabled {
  @apply opacity-50 cursor-auto;
}
.v-toggle input {
  outline: none;
  @apply m-0 p-0 w-0 h-0 opacity-0;
}
.v-toggle_thumb {
  transition: all 0.3s;
  border-radius: 50%;
  margin-top: -0.85rem;
  @apply w-7 h-7 absolute top-1/2 bg-blue;
}
.sub-info {
  color: theme('colors.blue.DEFAULT');
  @apply text-xs font-bold rounded-2xl py-1 px-2 border border-blue border-solid h-7;
}
.togg-bx span {
  color: theme('colors.gray.700');
}
.togg-bx span.active {
  color: theme('colors.black.DEFAULT');
}
</style>
