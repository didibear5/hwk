<script setup>
import Section from './Section.vue'

const base = import.meta.env.BASE_URL

const section4BrandItems = [
  {
    imgUrl1: '/img_section4_1.png',
    imgUrl2: '/img_section4_1@2x.png',
    content:
      'Lorem ipsum dolor sit amet, aliquip omnesque sit no, te pri vitae veniam intellegebat.',
  },
  {
    imgUrl1: '/img_section4_2.png',
    imgUrl2: '/img_section4_2@2x.png',
    content:
      ' It has roots in a piece of classical Latin literature from 45 BC, making it over 2000 years old.',
  },
]

const section4LogoItems = [
  {
    imgUrl1: '/img_section4_3.png',
    imgUrl2: '/img_section4_3@2x.png',
  },
  {
    imgUrl1: '/img_section4_4.png',
    imgUrl2: '/img_section4_4@2x.png',
  },
  {
    imgUrl1: '/img_section4_5.png',
    imgUrl2: '/img_section4_5@2x.png',
  },
  {
    imgUrl1: '/img_section4_6.png',
    imgUrl2: '/img_section4_6@2x.png',
  },
]
</script>
<template>
  <Section variant="secondary">
    <h2 class="text-h2-2 text-center">Section 4</h2>
    <div class="mt-10 grid grid-cols-1 gap-6 md:mt-13 lg:grid-cols-2 xl:gap-16">
      <div
        class="flex flex-col items-center rounded-lg bg-white p-6 sm:flex-row sm:gap-10 md:p-8 xl:p-13"
        v-for="(item, index) in section4BrandItems"
        :key="`section4-brand-${index}`"
      >
        <div class="shrink-0 lg:max-[1700px]:flex-1 lg:max-[1700px]:shrink">
          <img
            :src="item.imgUrl1"
            :srcset="`${base}${item.imgUrl1} 1x, ${base}${item.imgUrl2} 2x`"
          />
        </div>
        <div class="text-header4 lg:max-[1700px]:flex-2">
          {{ item.content }}
        </div>
      </div>
    </div>
    <div
      class="mt-20 grid grid-cols-1 items-center justify-items-center gap-2 gap-y-8 sm:grid-cols-2 sm:gap-y-12 lg:flex lg:flex-row lg:justify-between lg:px-5 xl:gap-0"
    >
      <img
        v-for="(item, index) in section4LogoItems"
        class="h-18 xl:h-auto"
        :key="`section4-logo-${index}`"
        :src="item.imgUrl1"
        :srcset="`${base}${item.imgUrl1} 1x, ${base}${item.imgUrl2} 2x`"
      />
    </div>
  </Section>
</template>
