<template>
  <table v-if="items.length > 0" :class="checkTableClasses">
    <thead>
      <tr>
        <th class="head-vert-cell">{{ cellHeading }}</th>
        <th
          v-for="(item, index) in items"
          :key="'header_' + index"
          :class="{ highlight: item.highlight }"
        >
          <atoms-image v-if="item.logo" :imageData="item.logo" />
          <strong v-if="item.name" class="name">{{ item.name }}</strong>
        </th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="field in getFieldKeys()" :key="field">
        <td>{{ fieldsMap[field] }}</td>
        <td
          v-for="(item, index) in items"
          :key="'item_' + item + '_' + index"
          :class="{ highlight: item.highlight }"
        >
          <span v-if="getType(item, field) === 'string'">{{
            getValue(item, field)
          }}</span>
          <span
            v-if="getType(item, field) === 'html'"
            v-html="getValue(item, field)"
          ></span>
          <span v-if="getType(item, field) === 'boolean'" class="icon-box">
            <img
              v-if="getValue(item, field) === true && item.highlight"
              :src="icon_success_ac"
              alt=""
            />
            <img
              v-else-if="getValue(item, field) === true"
              :src="icon_success"
              alt=""
            />
            <img v-else :src="icon_unsuccess" alt="" />
          </span>
        </td>
      </tr>
    </tbody>
    <tfoot v-if="items[0].footerLink">
      <tr>
        <td></td>
        <td v-for="(item, index) in items" :key="'footer-link-' + index">
          <NuxtLink :to="item.footerLink">{{ item.footerText }}</NuxtLink>
        </td>
      </tr>
    </tfoot>
  </table>
</template>

<script lang="ts">
interface fieldsMap {
  [index: string]: string
}
export default {
  name: 'compare-table',
  props: {
    cellHeading: {
      type: String,
    },
    fieldsMap: {
      type: Object as () => fieldsMap,
      default: () => [],
    },
    items: {
      type: Array as () => Array<{}>,
    },
    tableClasses: {
      type: Array,
      default: () => [],
    },
  },
  computed: {
    checkTableClasses() {
      return ['table-list', this.tableClasses]
    },
  },
  methods: {
    getFieldKeys() {
      return Object.keys(this.fieldsMap)
    },
    getType(item, field) {
      const htmlRegex = /(<(\/?[^>]+)>)/g

      switch (typeof item[field]) {
        case 'string':
          if (item[field]?.match(htmlRegex)) {
            return 'html'
          }
          return 'string'
        case 'boolean':
          return 'boolean'
        case 'object':
          return item[field] === null ? 'null' : 'object'
        default:
          return null
      }
    },
    getValue(item, field) {
      return item[field] || null
    },
  },
  data() {
    return {
      icon_success: '/img/icon-success.svg',
      icon_success_ac: '/img/icon-success-ac.svg',
      icon_unsuccess: '/img/icon-unsuccess.svg',
    }
  },
}
</script>
<style scoped>
.table-list {
  width: 1300px;
  @apply min-w-full table-fixed;
}
.compare-hero-table {
  max-width: 1076px;
  min-width: 360px;
  @apply w-full m-auto;
}
.table-list thead {
  @apply align-top;
}
.table-list th img {
  @apply text-center w-10 h-10 m-auto;
}
.table-list th,
.table-list td {
  font-size: 0.875rem;
  color: theme('colors.black.DEFAULT');
  @apply px-3 md:px-4 py-3 md:py-4 text-center border-b border-solid border-gray-200 leading-5;
}
.table-list td {
  @apply font-biennale font-light;
}
.table-list tfoot td {
  color: theme('colors.blue.DEFAULT');
  @apply border-0 py-5 md:py-8;
}
.table-list tfoot td a {
  max-width: 5rem;
  display: inline-block;
}
.compare-hero-table thead tr {
  @apply align-middle;
}
.compare-hero-table thead th {
  @apply text-sm md:text-xl;
}

.table-list td:first-child,
.table-list th:first-child {
  @apply md:w-52 text-left pl-0;
}
.compare-hero-table td:first-child,
.compare-hero-table th:first-child {
  @apply w-auto;
}
.compare-hero-table td:last-child,
.compare-hero-table th:last-child {
  background-color: rgba(240, 242, 246, 1);
}
td.highlight {
  color: theme('colors.green.DEFAULT');
}
.table-list:not(.compare-hero-table) thead th:first-child {
  @apply align-bottom pb-8 text-lg md:text-xl;
}
.table-list thead th:nth-child(even):not(.highlight),
.table-list tbody td:nth-child(even):not(.highlight) {
  background-color: rgba(240, 242, 246, 1);
}
.table-list thead th.highlight,
.table-list tbody td.highlight {
  @apply bg-white;
}
.name {
  @apply pt-2 block font-biennale font-medium;
}
.table-list thead th picture {
  @apply block m-auto w-10 h-10;
}
.icon-box {
  @apply block m-auto w-4 h-4;
}
.price {
  @apply block;
}
@media only screen and (max-width: calc(theme('screens.md') - 1px)) {
  .table-list {
    width: 1060px;
  }
  .compare-hero-table {
    max-width: 1076px;
    @apply w-full m-auto;
  }
  .table-list th,
  .table-list td {
    @apply text-xs;
  }
  .table-list td:first-child,
  .table-list th:first-child {
    width: 30vw;
  }
  .name {
    font-size: 0.8125rem;
  }
}
</style>
