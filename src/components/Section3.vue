<script setup>
import Section from './Section.vue'
import { ref, inject } from 'vue'

const base = import.meta.env.BASE_URL

const currentIndex = ref(0)
const toggleImage = (index) => {
  currentIndex.value = index
}

const deviceState = inject('deviceState')

const section3Items = [
  {
    imgUrl1: '/img_section3_1.jpg',
    imgUrl2: '/img_section3_1@2x.jpg',
    title: 'Where can I get some?',
    content:
      'Contrary to popular belief, Lorem Ipsum is not simply random text. It has roots in a piece of classical Latin literature from 45 BC, making it over 2000 years old.',
  },
  {
    imgUrl1: '/img_section3_2.jpg',
    imgUrl2: '/img_section3_2@2x.jpg',
    title: 'Where does it come from?',
    content:
      'Contrary to popular belief, Lorem Ipsum is not simply random text. It has roots in a piece of classical Latin literature from 45 BC, making it over 2000 years old.',
  },
]
</script>
<template>
  <Section>
    <div class="flex justify-between">
      <div class="flex items-center lg:mr-22 xl:mr-28 2xl:mr-32">
        <div class="lg:max-w-143">
          <h2 class="text-h2-2">Section 3</h2>
          <p class="text-body2 mt-2">
            Nor again is there anyone who loves or pursues or desires to obtain pain of itself,
            because it is pain, but because occasionally circumstances occur in which toil and pain
            can procure him some great pleasure.
          </p>
          <div class="mt-8">
            <div
              v-for="(item, index) in section3Items"
              :key="`section3-p-${index}`"
              class="border-0 border-l-5 border-solid pl-8 transition-all duration-500"
              :class="[
                currentIndex === index
                  ? 'border-[var(--color-primary)]'
                  : 'border-[var(--color-primary)]/0',
                index !== 0 ? 'mt-5' : '',
              ]"
            >
              <h4
                class="text-h4-2"
                :class="currentIndex === index ? 'opacity-100' : 'cursor-pointer opacity-50'"
                @click="toggleImage(index)"
              >
                {{ item.title }}
              </h4>
              <div
                class="text-body2 mt-2 grid transition-all duration-500"
                :class="currentIndex === index ? 'grid-rows-[1fr]' : 'grid-rows-[0fr]'"
              >
                <div class="overflow-hidden">
                  <p>{{ item.content }}</p>
                  <img
                    v-if="!deviceState.isLg"
                    class="mt-4 w-full rounded-lg transition-all duration-500"
                    :src="item.imgUrl1"
                    :srcset="`${base}${item.imgUrl1} 1x, ${base}${item.imgUrl2} 2x`"
                  />
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
      <div class="flex items-center" v-if="deviceState.isLg">
        <div class="relative">
          <img
            v-for="(item, index) in section3Items"
            :key="`section3-img-${index}`"
            class="max-w-none rounded-lg transition-all duration-500 max-[1700px]:w-full"
            :class="[
              currentIndex === index ? 'scale-100 opacity-100' : 'scale-95 opacity-0',
              index !== 0 ? 'absolute top-0' : '',
            ]"
            :src="item.imgUrl1"
            :srcset="`${base}${item.imgUrl1} 1x, ${base}${item.imgUrl2} 2x`"
          />
        </div>
      </div>
    </div>
  </Section>
</template>
