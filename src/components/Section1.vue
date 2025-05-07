<script setup>
import Section from './Section.vue'

const base = import.meta.env.BASE_URL

const section1Items = [
  {
    imgUrl1: '/img_section1_1.png',
    imgUrl2: '/img_section1_1@2x.png',
    title: 'Lorem Ipsum: common examples',
    content: `Most of its text is made up from sections 1.10.32–3 of Cicero's De finibus bonorum et malorum (On the Boundaries of Goods and Evils; finibus may also be translated as purposes).`,
  },
  {
    imgUrl1: '/img_section1_2.png',
    imgUrl2: '/img_section1_2@2x.png',
    title: 'Lorem Ipsum: translation',
    content: `No one rejects, dislikes, or avoids pleasure itself, because it is pleasure, but because those who do not know how to pursue pleasure rationally encounter consequences that are extremely painful.`,
  },
]
</script>
<template>
  <Section>
    <h2 class="text-h2 text-center">Section 1</h2>
    <p class="text-p2 m-auto mt-2 max-w-250 text-center">
      It is a long established fact that a reader will be distracted by the readable content of a
      page when looking at its layout.
    </p>
    <div class="mt-13 grid grid-cols-1 gap-6 lg:grid-cols-2">
      <div
        class="rounded-lg bg-[#E6E6E6]/50 text-center"
        v-for="(item, index) in section1Items"
        :key="`section1-${index}`"
      >
        <h4 class="text-h4 rounded-t-lg bg-black p-3 font-semibold text-white">
          {{ item.title }}
        </h4>
        <div class="px-8 py-10">
          <img
            :src="item.imgUrl1"
            :srcset="`${base}${item.imgUrl1} 1x, ${base}${item.imgUrl2} 2x`"
            alt="Server"
            class="m-auto"
          />
          <p class="text-p2 mt-6">
            {{ item.content }}
          </p>
        </div>
      </div>
    </div>
  </Section>
</template>
