<template>
  <section class="compare-secton">
    <heading-text
      v-if="heading"
      :title="heading.title"
      :subtitle="heading.subtitle"
      :description="heading.description"
      class="headingText large-desc"
      headerSize="large"
      container
    />
    <div class="wrapper">
      <h3 class="heading">{{ title }}</h3>
      <div class="compare-box">
        <compare-table
          :cellHeading="cellHeading"
          :fieldsMap="getFieldsMap()"
          :items="getData()"
          :tableClasses="tableClasses"
        />
      </div>
    </div>
  </section>
</template>

<script lang="ts">
import { HeadingType } from '~/types/HeadingType'

export const strapiName = 'component.competitors-pricing'

export enum pricingTypes {
  PricingFields = 'PricingFields',
  FeaturesFields = 'FeaturesFields',
}

export interface pricingFields {
  annualDiscount?: String
  upToTwentyFiveKSubs?: String
  subscriberCountMethod?: String
  upToFiftyKSubs?: String
  upToOneKSubs?: String
  nonProfitDiscount?: String
  upToFiveKSubs?: String
  upToTenKSubs?: String
  monthlyEmailSends?: String
  hasFreePlan?: Boolean
  dragAndDropEditor?: Boolean
  customHTMLEditor?: Boolean
  emailInteractiveSurveys?: Boolean
  emailVideoBlock?: Boolean
  emailMobileFriendly?: Boolean
  ecommerceCampaigns?: Boolean
  newsletterTemplates?: Boolean
}

export default {
  props: {
    heading: {
      type: Object as () => HeadingType,
      default: undefined,
    },
    title: {
      type: String,
    },
    cellHeading: {
      type: String,
    },
    type: {
      type: String as () => pricingTypes,
      default: pricingTypes,
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
      default: () => [],
    },
    showFooter: {
      type: Boolean,
      default: true,
    },
    showLogo: {
      type: Boolean,
      default: true,
    },
  },
  data() {
    return {
      fieldsName: {
        PricingFields: {
          monthlyEmailSends: 'Monthly email sends',
          subscriberCountMethod: 'Method of counting subscribers',
          upToOneKSubs: 'Up to 1,000 subscribers',
          upToFiveKSubs: 'Up to 5,000 subscribers',
          upToTenKSubs: 'Up to 10,000 subscribers',
          upToTwentyFiveKSubs: 'Up to 25,000 subscribers',
          upToFiftyKSubs: 'Up to 50,000 subscribers',
        },
        FeaturesFields: {
          dragAndDropEditor: 'Drag & drop editor',
          customHTMLEditor: 'Custom HTML editor',
          emailInteractiveSurveys: 'Interactive surveys in emails',
          emailVideoBlock: 'Video block in email',
          emailMobileFriendly: 'Mobile-fiendly emails',
          ecommerceCampaigns: 'E-Commerce campaigns',
          newsletterTemplates: 'Newsletter templates',
        },
      },
      bottomLink: {
        PricingFields: {
          personizely: 'View full pricing',
          others: 'View full comparison',
        },
        FeaturesFields: {
          personizely: 'Create free account',
          others: 'View full comparison',
        },
      },
    }
  },
  computed: {
    visibleItems() {
      const visibleSlugs = this.visibleCompetitors.map((o) => o.slug)

      return this.items.filter((o) => visibleSlugs.includes(o.slug))
    },
  },
  methods: {
    getData() {
      const elements = []
      this.visibleItems.forEach((item) => {
        const fields = {}
        this.getFieldKeys().forEach((fieldKey) => {
          fields[fieldKey] = item[this.type]?.[fieldKey]
        })
        const highlight = item.name.toLowerCase() === 'personizely'
        elements.push({
          id: item.id,
          name: item.name,
          highlight,
          ...fields,
          logo: this.showLogo
            ? item.logo || {
                original: { url: `/img/logo-${item.slug}.svg` },
                isMock: true,
              }
            : null,
          footerLink: this.showFooter
            ? this.getLink(highlight, item.slug)
            : null,
          footerText: this.showFooter
            ? highlight
              ? this.bottomLink[this.type]?.personizely
              : this.bottomLink[this.type]?.others
            : null,
        })
      })
      return elements
    },
    getFieldKeys() {
      return this.fieldsName[this.type]
        ? Object.keys(this.fieldsName[this.type])
        : []
    },
    getFieldsMap() {
      return this.fieldsName[this.type] || []
    },
    getLink(highlight: boolean, slug: string) {
      return highlight ? '/pricing-list' : `/competitor/${slug}`
    },
  },
}
</script>
<style scoped>
.compare-secton {
  @apply bg-gray-100 pb-12 pt-2 md:py-16 overflow-hidden;
}
.wrapper {
  max-width: 1360px;
  @apply px-5 m-auto w-full;
}
h3 {
  @apply font-biennale font-medium text-center text-xl md:text-3xl mb-8 md:mb-12;
}
.compare-box {
  @apply w-full overflow-x-auto;
}
.compare-box::-webkit-scrollbar {
  @apply h-1;
}
.compare-box::-webkit-scrollbar-track {
  border-radius: 4px;
  @apply bg-gray-200;
}
.compare-box::-webkit-scrollbar-thumb {
  border-radius: 2px;
  @apply bg-blue;
}
</style>
