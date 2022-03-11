<template>
  <section id="hero" class="compare-secton mb-10 md:mb-20">
    <div class="wrapper">
      <integration-hero
        :title="heading.title"
        :description="heading.description"
        :logoImage="competitorsLogo"
      />
      <div class="compare-box">
        <compare-table
          :cellHeading="cellHeading"
          :fieldsMap="getFieldsMap()"
          :items="getData()"
          :tableClasses="tableClasses"
        />
      </div>
      <div class="button-box text-center py-10">
        <atoms-button
          v-if="button"
          :color="button.color"
          :href="button.href"
          :rounded="button.rounded"
          :size="button.size"
          class="mx-auto"
        >
          {{ button.text }}
        </atoms-button>
      </div>
    </div>
  </section>
</template>

<script lang="ts">
import { HeadingType } from '~/types/HeadingType'
import CompareTable from './CompareTable.vue'
import { ButtonType } from '~/types/ButtonType'

export const strapiName = 'component.competitors-t1'

export interface pricingFields {
  annualDiscount?: String
  upToTwentyFiveKSubs?: String
  subscriberCountMethod?: String
  upToFiftyKSubs?: String
  nonProfitDiscount?: String
  upToFiveKSubs?: String
  upToTenKSubs?: String
  monthlyEmailSends?: String
  hasFreePlan?: Boolean
}

export default {
  components: { CompareTable },
  name: 'compare-hero',
  props: {
    heading: {
      type: Object as () => HeadingType,
    },
    cellHeading: {
      type: String,
    },
    items: {
      type: Array as () => Array<pricingFields>,
    },
    visibleCompetitors: {
      type: Array,
      default: () => [],
    },
    tableClasses: {
      type: Array,
      default: () => ['compare-hero-table'],
    },
    button: {
      type: Object as () => ButtonType,
    },
  },
  data() {
    return {
      fieldsName: {
        subscriberCountMethod: 'Method of counting subscribers',
        monthlyEmailSends: 'Monthly email sends',
        hasFreePlan: 'Free plan',
        upToFiveKSubs: 'Up to 5,000 subscribers',
        upToTenKSubs: 'Up to 10,000 subscribers',
        upToTwentyFiveKSubs: 'Up to 25,000 subscribers',
        upToFiftyKSubs: 'Up to 50,000 subscribers',
        annualDiscount: 'Annual discount',
        nonProfitDiscount: 'Non-profit discount',
      },
    }
  },
  computed: {
    competitorsLogo() {
      return this.items[1]?.logo
        ? this.items[1].logo
        : this.items[1]?.slug
        ? {
            original: { url: `/img/logo-${this.items[1].slug}.svg` },
            isMock: true,
          }
        : null
    },
    visibleItems() {
      const visibleSlugs = this.visibleCompetitors.map((o) => o.slug)

      return this.items.filter((o) => visibleSlugs.includes(o.slug))
    },
  },
  methods: {
    getData() {
      const fieldPath = 'PricingFields'
      let elements = []
      this.visibleItems.forEach((item) => {
        let fields = {}
        this.getFieldKeys().forEach((fieldKey) => {
          fields[fieldKey] = item[fieldPath][fieldKey]
        })
        let highlight = item.name.toLowerCase() === 'personizely'
        elements.push({
          id: item.id,
          name: item.planName,
          highlight: highlight,
          ...fields,
        })
      })
      return elements
    },
    getFieldKeys() {
      return Object.keys(this.fieldsName)
    },
    getFieldsMap() {
      return this.fieldsName || []
    },
  },
}
</script>
<style scoped>
.compare-secton {
  @apply bg-gray-100 py-16 overflow-hidden;
}
.wrapper {
  max-width: 1360px;
  @apply px-5 m-auto w-full;
}
.compare-secton >>> .integration-hero-container {
  @apply mb-20 lg:mb-20 md:mb-4 lg:pb-1;
}
</style>
