<template>
  <div ref="panel-nav" :class="className" class="panel-nav py-6 md:py-8 z-100">
    <nav class="flex justify-between flex-wrap md:flex-nowrap items-center">
      <div v-scroller="'fadein-left'" class="logo flex-none w-36 relative">
        <NuxtLink to="/">
          <svg
            width="147"
            height="30"
            viewBox="0 0 147 30"
            fill="none"
            xmlns="http://www.w3.org/2000/svg"
          >
            <g clip-path="url(#clip0_663_1797)">
              <path
                d="M14.9989 0C6.71573 0 0 6.71574 0 14.9989C0 23.282 6.71573 29.9977 14.9989 29.9977C23.282 29.9977 29.9977 23.282 29.9977 14.9989C30 6.71574 23.2843 0 14.9989 0ZM14.9851 2.07307C22.1402 2.07307 27.9407 7.87354 27.9407 15.0286C27.9407 22.1837 22.1402 27.9841 14.9851 27.9841C7.83006 27.9841 2.02959 22.1837 2.02959 15.0286C2.02959 7.87354 7.83006 2.07307 14.9851 2.07307Z"
                fill="#425DF9"
              />
              <path
                d="M14.9852 4.21741C9.01544 4.21741 4.17371 9.05686 4.17371 15.0289C4.17371 20.9987 9.01315 25.8405 14.9829 25.8405C20.9527 25.8405 25.7945 21.001 25.7945 15.0289C25.7968 9.05914 20.9573 4.21741 14.9852 4.21741ZM14.8983 6.35912C19.6645 6.35912 23.5292 10.2238 23.5292 14.99C23.5292 19.7563 19.6645 23.621 14.8983 23.621C10.1321 23.621 6.26737 19.7563 6.26737 14.99C6.26737 10.2238 10.1321 6.36141 14.8983 6.35912Z"
                fill="#425DF9"
              />
              <path
                d="M14.8982 8.57364C11.3538 8.57364 8.47989 11.4476 8.48218 14.9919C8.48218 18.5363 11.3561 21.4079 14.8982 21.4079C18.4425 21.4079 21.3164 18.534 21.3164 14.9919C21.3164 11.4476 18.4425 8.57364 14.8982 8.57364ZM14.9027 10.6742C17.2801 10.6742 19.209 12.6008 19.209 14.9805C19.209 17.3579 17.2824 19.2868 14.9027 19.2868C12.5253 19.2868 10.5964 17.3602 10.5964 14.9805C10.5964 12.6031 12.5253 10.6742 14.9027 10.6742Z"
                fill="#425DF9"
              />
              <path
                d="M10.5964 15.1203H8.48218V23.3508H10.5964V15.1203Z"
                fill="#425DF9"
              />
              <path
                d="M14.9073 16.7148C15.8475 16.7148 16.6097 15.9526 16.6097 15.0124C16.6097 14.0722 15.8475 13.31 14.9073 13.31C13.9671 13.31 13.205 14.0722 13.205 15.0124C13.205 15.9526 13.9671 16.7148 14.9073 16.7148Z"
                fill="#425DF9"
              />
              <path
                class="mob-change"
                d="M49.9069 14.6576C49.9069 17.9754 47.5822 20.4672 44.4131 20.4672C42.8068 20.4672 41.5186 19.8334 40.6514 18.7351V23.9956H38.4113V9.08138H40.482V10.8341C41.3698 9.58707 42.7427 8.84799 44.4543 8.84799C47.6463 8.84799 49.9069 11.3421 49.9069 14.6576ZM47.6874 14.6576C47.6874 12.4404 46.1864 10.8135 44.1385 10.8135C42.0265 10.8135 40.5461 12.3969 40.5461 14.6576C40.5461 16.9183 42.0037 18.4811 44.1385 18.4811C46.1681 18.4811 47.6874 16.8565 47.6874 14.6576Z"
                fill="#0C0E12"
              />
              <path
                class="mob-change"
                d="M56.6846 18.4811C58.3526 18.4811 59.2839 17.8678 59.7896 16.7055L61.627 17.8678C60.7827 19.346 59.2816 20.4672 56.6205 20.4672C53.1128 20.4672 50.7903 17.9731 50.7903 14.6576C50.7903 11.4244 53.305 8.82733 56.4512 8.82733C59.8949 8.82733 62.0297 11.5319 62.0297 14.4059C62.0297 14.7857 62.0091 15.1884 61.9885 15.3989H53.0098C53.3462 17.2981 54.8037 18.4811 56.6846 18.4811ZM59.8331 13.6874C59.5379 11.8065 58.2497 10.6441 56.5381 10.6441C54.806 10.6441 53.369 11.763 53.0304 13.6874H59.8331Z"
                fill="#0C0E12"
              />
              <path
                class="mob-change"
                d="M69.0474 8.82733V10.9187C67.0613 10.9393 65.7524 12.1223 65.7524 13.6874V20.2155H63.5123V9.08132H65.6243V10.4977C66.3634 9.54581 67.5875 8.82733 69.0474 8.82733Z"
                fill="#0C0E12"
              />
              <path
                class="mob-change"
                d="M69.2144 17.6803L71.2417 16.8977C71.5803 17.996 72.5299 18.6299 73.9669 18.6299C75.2139 18.6299 76.017 18.1013 76.017 17.1929C76.017 14.7629 69.7429 15.8612 69.7429 12.0377C69.7429 10.0516 71.3904 8.84799 73.9257 8.84799C76.017 8.84799 77.5181 9.69232 78.0032 11.1934L75.9759 11.9759C75.6372 11.0675 74.9187 10.6236 73.8845 10.6236C72.7427 10.6236 72.1089 11.1316 72.1089 11.9118C72.1089 14.1931 78.383 12.9461 78.383 17.0236C78.383 19.1996 76.6074 20.4672 73.9051 20.4672C71.5391 20.4672 69.807 19.4971 69.2144 17.6803Z"
                fill="#0C0E12"
              />
              <path
                class="mob-change"
                d="M79.0466 14.6576C79.0466 11.3192 81.4767 8.84799 84.8997 8.84799C88.3434 8.84799 90.7734 11.3192 90.7734 14.6576C90.7734 17.9754 88.3434 20.4672 84.8997 20.4672C81.4744 20.4672 79.0466 17.9754 79.0466 14.6576ZM88.531 14.6576C88.531 12.4175 87.0735 10.8341 84.918 10.8341C82.7626 10.8341 81.2844 12.4175 81.2844 14.6576C81.2844 16.8542 82.7626 18.4605 84.918 18.4605C87.0529 18.4605 88.531 16.8771 88.531 14.6576Z"
                fill="#0C0E12"
              />
              <path
                class="mob-change"
                d="M102.569 13.3489V20.2156H100.329V13.7493C100.329 11.9119 99.2304 10.8136 97.4548 10.8342C95.7867 10.8342 94.5603 12.0606 94.5397 13.4335V20.2156H92.2996V9.08144H94.4115V10.4978C95.1712 9.52534 96.4388 8.82974 98.0886 8.82974C100.878 8.82746 102.569 10.6237 102.569 13.3489Z"
                fill="#0C0E12"
              />
              <path
                class="mob-change"
                d="M104.088 5.59441C104.088 4.66542 104.807 3.98813 105.715 3.98813C106.623 3.98813 107.342 4.66542 107.342 5.59441C107.342 6.5234 106.623 7.15722 105.715 7.15722C104.807 7.15951 104.088 6.52569 104.088 5.59441ZM104.596 9.08156H106.836V20.2157H104.596V9.08156Z"
                fill="#0C0E12"
              />
              <path
                class="mob-change"
                d="M116.856 18.3989V20.2157H107.836V18.6095L113.9 10.8984H108.111V9.08157H116.625V10.7496L110.605 18.3967H116.856V18.3989Z"
                fill="#0C0E12"
              />
              <path
                class="mob-change"
                d="M122.885 18.4811C124.553 18.4811 125.485 17.8678 125.99 16.7055L127.828 17.8678C126.983 19.346 125.482 20.4672 122.821 20.4672C119.314 20.4672 116.991 17.9731 116.991 14.6576C116.991 11.4244 119.506 8.82733 122.654 8.82733C126.098 8.82733 128.233 11.5319 128.233 14.4059C128.233 14.7857 128.212 15.1884 128.192 15.3989H119.213C119.547 17.2981 121.005 18.4811 122.885 18.4811ZM126.034 13.6874C125.739 11.8065 124.45 10.6441 122.739 10.6441C121.007 10.6441 119.57 11.763 119.231 13.6874H126.034Z"
                fill="#0C0E12"
              />
              <path
                class="mob-change"
                d="M129.738 4.77045H131.979V20.2132H129.738V4.77045Z"
                fill="#0C0E12"
              />
              <path
                class="mob-change"
                d="M144.14 9.08157L139.747 20.2157L138.269 23.9981H136.072L137.594 20.2157H136.96L132.818 9.08157H135.12L138.353 18.3761L141.818 9.08157H144.14Z"
                fill="#0C0E12"
              />
              <path
                class="mob-change"
                d="M143.284 19.0326C143.284 18.2089 143.898 17.6163 144.678 17.6163C145.481 17.6163 146.071 18.2066 146.071 19.0326C146.071 19.8152 145.479 20.4055 144.678 20.4055C143.895 20.4055 143.284 19.8129 143.284 19.0326Z"
                fill="#0C0E12"
              />
            </g>
            <defs>
              <clipPath id="clip0_663_1797">
                <rect width="146.074" height="30" fill="white" />
              </clipPath>
            </defs>
          </svg>
        </NuxtLink>
      </div>
      <div class="nav-box z-10">
        <div class="box flex-grow justify-center">
          <div
            class="heading-mob flex md:hidden justify-between items-center mb-3"
          >
            <h2 ref="menu-header">Menu</h2>
            <atoms-button
              class="back-btn"
              :size="btnSizeSmall"
              :color="btnColorNavy"
              :callback="{ after: BackfromDrop }"
              v-show="mobileNavigation.showBackButton"
              >Back</atoms-button
            >
          </div>
          <ul
            ref="nav-list"
            class="nav-list static flex flex-col md:flex-row justify-center items-start md:items-center flex-nowrap"
            v-if="navigation !== null"
          >
            <li
              v-for="item in navigation.navigation.items"
              :key="item.id"
              @click="DropOpenMenu(item.id)"
              @mouseenter="hover"
              @mouseleave="out"
              class="col-item py-2 px-4"
            >
              <NuxtLink
                v-if="item.children.length === 0"
                class="flex justify-between"
                :to="item.url"
              >
                <span class="px-1">{{ item.text }}</span>
              </NuxtLink>
              <div v-else class="flex justify-between box-with-drop">
                <span class="px-1" :ref="'menu-header-' + item.id">{{
                  item.text
                }}</span>
                <picture
                  v-if="item.children.length > 0"
                  class="flex flex-col items-center justify-center"
                >
                  <source
                    media="(max-width:767px)"
                    srcset="/img/arrow-mob.svg"
                  />
                  <img class="px-1" src="@/assets/img/icons/arrow.svg" />
                </picture>
              </div>
              <div
                v-if="item.children.length > 0"
                class="drop"
                :ref="'menu-drop-' + item.id"
              >
                <div class="drop-menu">
                  <div class="drop-heading">
                    <h2>{{ item.title }}</h2>
                    <p>{{ item.description }}</p>
                  </div>
                  <div class="drop-list">
                    <ul>
                      <li
                        v-for="child in item.children"
                        :key="child.id"
                        @click.stop="goTo(child.url)"
                      >
                        <NuxtLink :to="child.url">
                          <div class="drop-item">
                            <div v-if="child.icon" class="item-img">
                              <atoms-image
                                :imageData="getChildIcon(child.icon)"
                              />
                            </div>
                            <div class="item-text">
                              <span>{{ child.text }}</span>
                              <p>{{ child.description }}</p>
                            </div>
                          </div>
                        </NuxtLink>
                      </li>
                    </ul>
                  </div>
                </div>
              </div>
            </li>
          </ul>
          <div class="mob-btn-block flex md:hidden w-full flex-col">
            <atoms-button
              class="sign-in-btn"
              :color="btnColotTransparent"
              :size="btnSizeSmall"
              :href="signIn.data.url"
              >{{ signIn.data.text }}
            </atoms-button>
            <atoms-button
              class="sign-up-btn ml-1"
              :color="btnColorBlue"
              :size="btnSizeSmall"
              >Sign Up
            </atoms-button>
          </div>
          <div class="social text-center hidden">
            <p class="text-white mb-3">Follow us</p>
            <div class="flex justify-center">
              <SocialMedia />
            </div>
          </div>
        </div>
      </div>
      <div
        v-scroller="'fadein-right'"
        class="btn-box flex items-center flex-row lg:flex-none h-6 text-right"
      >
        <atoms-button
          class="sign-in-btn"
          :color="btnColotTransparent"
          :size="btnSizeSmall"
          :href="signIn.data.url"
          :external="false"
          :url="
            (formattedUrl = {
              url: ``,
            })
          "
          >{{ signIn.data.text }}
        </atoms-button>
        <atoms-button
          class="sign-up-btn ml-1"
          :color="btnColorBlue"
          :size="btnSizeSmall"
          >Sign Up
        </atoms-button>
        <span
          class="mobileBtn ml-1 bg-blue rounded-md flex w-9 h-9 items-center justify-center md:hidden cursor-pointer relative z-10"
          @click="OpenCloseMobileMenu"
        >
          <svg
            xmlns="http://www.w3.org/2000/svg"
            xmlns:xlink="http://www.w3.org/1999/xlink"
            width="13px"
            height="11px"
          >
            <path
              fill-rule="evenodd"
              fill="rgb(255, 255, 255)"
              d="M-0.000,-0.000 L13.000,-0.000 L13.000,1.000 L-0.000,1.000 L-0.000,-0.000 Z"
            />
            <path
              fill-rule="evenodd"
              fill="rgb(255, 255, 255)"
              d="M-0.000,4.000 L13.000,4.000 L13.000,5.000 L-0.000,5.000 L-0.000,4.000 Z"
            />
            <path
              fill-rule="evenodd"
              fill="rgb(255, 255, 255)"
              d="M-0.000,8.000 L13.000,8.000 L13.000,9.000 L-0.000,9.000 L-0.000,8.000 Z"
            />
          </svg>
        </span>
      </div>
    </nav>
  </div>
</template>

<script lang="ts">
import { ref, useFetch } from '@nuxtjs/composition-api'
import { btnColor, btnSize } from '@/components/atoms/Button.vue'
import config from '@/tailwind.config.js'

enum navPosition {
  relative = 'relative bg-gray-100',
  absolute = 'absolute w-full left-0 top-0',
}

export default {
  setup() {
    const navigation = ref(null)
    const signIn = ref(null)

    useFetch(async ({ $strapi }) => {
      navigation.value = await $strapi.find('navigation')
      signIn.value = await $strapi.find('sign-in-link')
    })
    return { navigation, signIn }
  },
  props: {
    absolute: {
      type: Boolean,
      default: true,
    },
    relative: {
      type: Boolean,
      default: false,
    },
  },

  data() {
    return {
      mobileNavigation: {
        isOpen: false,
        showBackButton: false,
      },
      isSticky: false,
      stickyClass: 'is-sticky',
      btnColorBlue: btnColor.blue,
      btnColorNavy: btnColor.navy,
      btnColotTransparent: btnColor.transparent,
      btnSizeSmall: btnSize.small,
      strapiUrl: process.env.STRAPI_URL,
    }
  },

  computed: {
    className() {
      return {
        [this.stickyClass]: this.isSticky,
        ...this.checkClasses(),
      }
    },
  },

  methods: {
    hover: (e) => e.target.classList.add('hover'),
    out: (e) => e.target.classList.remove('hover'),
    handleScroll() {
      let scroll = window.scrollY
      this.isSticky = scroll > 5
    },
    checkClasses() {
      const classes = {}

      if (this.relative) {
        classes[navPosition.relative] = true
      } else {
        classes[navPosition.absolute] = true
      }
      return classes
    },
    OpenCloseMobileMenu() {
      this.mobileNavigation.isOpen = !this.mobileNavigation.isOpen
      this.ChangeClassesMobileMenu()
    },
    ChangeClassesMobileMenu() {
      const panel = this.$refs['panel-nav']

      if (this.mobileNavigation.isOpen) {
        panel?.classList?.add('active')
        document.body.classList?.add('fixedBody')
      } else {
        panel?.classList?.remove('active')
        document.body.classList?.remove('fixedBody')
        this.BackfromDrop()
      }
    },
    DropOpenMenu(index) {
      if (document?.defaultView?.innerWidth > 768) return

      if (this.$refs[`menu-drop-${index}`] === undefined) {
        return this.OpenCloseMobileMenu()
      }

      this.$refs['nav-list']?.classList?.add('drop-slide')
      this.$refs[`menu-drop-${index}`][0]?.classList?.add('drop-active')

      this.mobileNavigation.showBackButton = true
      this.changeHeader(this.$refs[`menu-header-${index}`][0].innerText)
    },
    BackfromDrop() {
      this.$refs['panel-nav']
        .querySelectorAll('.drop-slide, .drop-active')
        .forEach((slide) => slide.classList.remove('drop-slide', 'drop-active'))

      this.mobileNavigation.showBackButton = false
      this.changeHeader('Menu')
    },
    changeHeader(newHeader: string) {
      this.$refs['menu-header'].innerText = newHeader
    },
    goTo(url: string) {
      if (this.isMobile()) {
        this.OpenCloseMobileMenu()
      }
      this.$router.push(url)
      setTimeout(() => {
        this.$refs['panel-nav']
          .querySelector('li.hover')
          ?.classList.remove('hover')
      }, 200)
    },
    isMobile() {
      return (
        document?.defaultView?.innerWidth <=
        parseInt(config?.theme?.screens?.md)
      )
    },
    getChildIcon(icon) {
      return { original: { url: icon.url } }
    },
  },
  mounted() {
    window?.addEventListener('scroll', this.handleScroll)
  },
}
</script>
<style>
.fixedBody {
  @apply overflow-hidden;
}
</style>

<style scoped>
nav {
  @apply m-auto h-full px-5 md:px-0 relative z-20;

  max-width: 1440px;
  padding: 0 4.5rem;
}
.nav-box {
  @apply -mr-20;
}
.panel-nav {
  --nav-transitions: 1;

  transition: all calc(0.3s * var(--nav-transitions));
}
@media (prefers-reduced-motion: reduce) {
  .panel-nav {
    --nav-transitions: 0;
  }
}
.panel-nav.is-sticky {
  box-shadow: 0 0 40px rgba(12, 14, 18, 0.04);

  @apply fixed w-full h-20 left-0 top-0 z-10 bg-white py-3 md:py-4;
}
.logo {
  z-index: 100;
}
.btn-box {
  min-width: 190px;
  transition: all calc(0.5s * var(--nav-transitions));
  @apply w-11 h-5 text-right flex justify-end;
}
.panel-nav.is-sticky .btn-box {
  min-width: 190px;
  @apply flex justify-start;
}
.row {
  @apply grid grid-cols-3 gap-x-3;
}
.ul-list {
  @apply grid grid-cols-5 gap-x-5;
  @apply flex flex-nowrap;
}
.col-item {
  @apply text-base hover:text-blue;
}
.nav-list li {
  @apply z-20;
}

.drop-menu li a {
  color: theme('colors.gray.700');
  @apply md:rounded-md hover:text-white md:hover:bg-gray-100;
}
.drop-menu li span {
  font-size: 1.0625rem;
  line-height: 1.1rem;
  color: theme('colors.black.DEFAULT');
  @apply block font-biennale   whitespace-nowrap md:pb-2;
}
.nav-list > li > div > span {
  @apply relative;
}
.nav-list > li > div > span::after {
  content: '';
  border-left: 9px solid transparent;
  border-right: 9px solid transparent;
  border-bottom: 9px solid white;
  @apply absolute w-2 h-2 -bottom-8 left-1/2 hidden -ml-2 z-50;
}
.nav-list li.hover div span::after {
  @apply md:block;
}
.is-sticky .nav-list > li > div > span::after {
  @apply -bottom-9;
}
.drop {
  padding: 0 4.5rem;
  @apply absolute top-full left-0 md:w-full z-20;
}
.drop-menu {
  box-shadow: 0 32px 64px rgba(12, 14, 18, 0.08);
  border-radius: 10px;
  @apply md:rounded-xl md:bg-white md:mt-6 md:p-2 hidden;
}
.panel-nav.is-sticky .drop {
  top: 90%;
}
.panel-nav.is-sticky .drop-menu {
  @apply md:mt-7;
}
.nav-list > li.hover .drop-menu {
  @apply flex;
}
.drop-heading {
  @apply w-2/6 px-10 py-10 bg-gray-100 rounded-lg hidden md:block;

  background-image: url('/img/drop-heading.png');
  background-repeat: no-repeat;
  min-height: 408px;
}
.drop-heading h2 {
  font-size: 2rem;
  @apply m-0 mb-4 font-biennale font-medium;
}
.drop-heading p {
  color: theme('colors.gray.700');
  @apply mb-8;
}
.drop-list {
  @apply w-full md:w-4/6 p-0 md:p-8 md:pb-4;
}
.drop-list ul {
  @apply md:grid md:grid-cols-2;
}
.drop-list ul li a {
  @apply rounded-xl mb-0 md:mb-2 mr-0 md:mr-2 block;
}
.drop-list ul li.hover a {
  @apply md:bg-gray-100;
}
.drop-list ul li .item-text span:hover {
  color: theme('colors.blue.DEFAULT');
}
.drop-item {
  @apply flex p-0 md:p-5;
}
.item-img {
  min-width: 48px;
  @apply mr-5 hidden md:block;
}
.item-text p {
  @apply hidden md:block;

  color: theme('colors.gray.700');
  font-size: 0.9375rem;
  line-height: 1.4rem;
}
nav > .btn-box > .btn.sign-up-btn {
  @apply hidden;
}
.is-sticky nav > .btn-box > .sign-up-btn {
  @apply flex;
}
@media only screen and (max-width: calc(theme('screens.xl') - 1px)) {
  nav {
    @apply px-12;
  }
}
@media only screen and (max-width: calc(theme('screens.lg') - 1px)) {
  .drop-list {
    @apply p-2;

    width: 75%;
  }
  .drop-item {
    @apply md:p-2;
  }
  .nav-list ul {
    grid-template-columns: repeat(2, minmax(0, 0.5fr));
  }
  .drop-heading {
    width: 25%;
    @apply px-5;
  }
}
@media only screen and (max-width: calc(theme('screens.md') - 1px)) {
  .nav-box {
    @apply order-2 w-full h-screen -left-full top-0 bg-navy-900 fixed flex flex-col justify-start pt-32 px-5;

    transition: all calc(0.5s * var(--nav-transitions));
  }
  .panel-nav {
    @apply absolute z-10 py-5 px-0;
  }
  .panel-nav.active .nav-box {
    @apply left-0;

    transition: all calc(0.5s * var(--nav-transitions));
  }
  .nav-list {
    transition: all calc(0.5s * var(--nav-transitions));
    @apply relative left-0;
  }
  .drop-slide {
    transition: all calc(0.5s * var(--nav-transitions));
    left: 110%;
  }
  nav {
    @apply px-6;
  }
  .nav-list li .drop-menu {
    @apply block;
  }
  .nav-list .drop {
    max-width: 100%;
    left: -220%;
    transition: all calc(0.5s * var(--nav-transitions));
    padding: 0;
    @apply absolute top-0  w-full;
  }
  .drop-slide .drop-active {
    left: -110%;
    @apply top-0;
  }
  .nav-list li {
    color: theme('colors.white.DEFAULT');
    @apply border-b border-solid border-white border-opacity-25 w-full px-0 py-0;
  }
  .box-with-drop,
  .drop-menu li a span,
  .nav-list li a {
    color: theme('colors.white.DEFAULT');
    @apply w-full flex text-2xl py-3 transition-all cursor-pointer;
  }
  .drop-list {
    width: 100%;
  }
  .btn-box,
  .panel-nav.is-sticky .btn-box {
    height: 36px;
    z-index: 11;
    min-width: 130px;
  }
  .mob-btn-block .sign-in-btn {
    color: theme('colors.white.DEFAULT');
    @apply mb-2;
  }
  .mob-btn-block .sign-up-btn {
    @apply ml-0;
  }
  .btn-box .sign-up-btn,
  .is-sticky nav > .btn-box > .sign-up-btn {
    @apply hidden;
  }
  .btn-box .sign-in-btn {
    transition: all calc(0.5s * var(--nav-transitions));
    transition-delay: calc(0.2s * var(--nav-transitions));

    @apply visible;
  }
  .panel-nav.active .btn-box .sign-in-btn {
    transition: none;

    @apply invisible;
  }

  .logo .mob-change {
    transition: all calc(0.5s * var(--nav-transitions));
  }
  .active .logo .mob-change {
    fill: white;
  }
  .active .social {
    width: 114px;
    margin-left: -57px;
    @apply block absolute bottom-10 left-1/2;
  }
  .active .social li {
    @apply px-3;
  }
  .active .social li rect {
    transition: all calc(0.5s * var(--nav-transitions));
  }
  .active .social li:hover rect {
    fill: theme('colors.blue.DEFAULT');
  }
  .mobileBtn span path {
    transition: transform calc(0.25s * var(--nav-transitions));
    transition: all calc(0.5s * var(--nav-transitions));
  }
  .active .mobileBtn path:nth-of-type(1) {
    transform: rotate(45deg);
    transform-origin: 0 3px;
  }
  .active .mobileBtn path:nth-of-type(2) {
    display: none;
  }
  .active .mobileBtn path:nth-of-type(3) {
    transform-origin: 3px 7px;
    transform: rotate(-45deg);
  }
  .heading-mob h2 {
    color: theme('colors.blue.DEFAULT');
    @apply text-4xl;
  }
  .item-text {
    @apply w-full border-0;
  }
  .drop-list ul li .item-text span:hover {
    color: theme('colors.white.DEFAULT');
  }
  .mob-btn-block {
    width: 350px;
    margin-left: -175px;
    @apply absolute bottom-32 left-1/2;
  }
  .mob-btn-block .btn {
    width: 100%;
  }
}
@media (orientation: landscape) and (max-width: calc(theme('screens.lg') - 1px)) {
  .drop-list {
    max-height: 80vh;
    @apply overflow-y-auto p-0;
  }
  .drop-heading {
    @apply p-5;
  }
}
@media (max-height: calc(theme('screens.md') - 1px)) and (max-width: calc(theme('screens.md') - 1px)) {
  .nav-box {
    @apply overflow-y-auto pt-20;
  }
  .nav-box .box {
    height: 700px;
    padding-bottom: 20rem;
    position: relative;
  }
}
.sing-in-btn {
  @apply hidden h-9;
}
.btn {
  @apply flex items-center justify-center leading-3;

  white-space: nowrap;
}
</style>
