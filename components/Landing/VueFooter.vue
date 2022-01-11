<template>
  <footer
    class="
      relative
      pt-[52px]
      pb-[36px]
      lg:pt-[140px] lg:pb-[70px]
      overflow-hidden
    "
  >
    <img
      src="~/assets/img/landing/footer-bg.png"
      alt=""
      class="
        hidden
        lg:block
        absolute
        left-[50%]
        top-[13px]
        translate-x-[-50%]
        max-w-none
      "
    />

    <div class="relative container flex flex-col items-center">
      <nuxt-link to="/">
        <img
          src="~/assets/img/logo.svg"
          class="w-[229px] h-[135px] lg:w-[282px] lg:h-[166px]"
          alt="Candy Shop"
          width="229"
          height="135"
        />
      </nuxt-link>

      <div class="hidden xl:flex mt-[38px] flex items-center">
        <component-link
          :route="navigation[0].route"
          :href="navigation[0].href"
          :disabled="navigation[0].disabled"
          :disabled-title="navigation[0].disabledTitle"
          :class="{
            'no-underline hover:underline': $route.name !== navigation[0].route,
          }"
          class="px-[31px] font-bold"
        >
          <span
            class="
              absolute
              top-[-20px]
              border-white border
              rounded-[26px]
              px-[6px]
              z-10
              bg-[#7B1FCB]
              text-xs
            "
            v-if="navigation[0].route"
          >
            coming soon
          </span>
          <span :disabled="navigation[0].route">Lounch APP</span>
        </component-link>
        <div class="flex items-center my-5 mx-auto justify-center">
          <div
            v-for="(social, socialKey) in socials"
            :key="socialKey"
            class="text-2xl px-5"
          >
            <social-link
              :href="social.href"
              :icon="social.icon"
              class="text-white hover:opacity-50"
            />
          </div>
        </div>
      </div>

      <div class="mt-[13px] xl:mt-[31px] text-[13px] leading-[21px]">
        ©2021 Candyshop
      </div>
    </div>
  </footer>
</template>

<script lang="ts">
import Vue from 'vue'
import ComponentLink from '~/components/ComponentLink.vue'

export default Vue.extend({
  components: { ComponentLink },
  computed: {
    navigation() {
      return this.$store.getters['app/menu'].landingNavigation
    },
    socials() {
      return this.$store.getters['app/menu'].socials
    },
  },
})
</script>
