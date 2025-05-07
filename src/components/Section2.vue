<script setup>
import Section from './Section.vue'
import Button from './Button.vue'
import { inject } from 'vue'

const deviceState = inject('deviceState')

const section2Items = [
  {
    step: 'Stage 1',
    title: 'Lorem Ipsum',
    content:
      'Lorem Ipsum comes from sections 1.10.32 and 1.10.33 of "de Finibus Bonorum et Malorum" (The Extremes of Good and Evil) by Cicero, written in 45 BC.',
  },
  {
    step: 'Stage 2',
    title: 'Lorem Ipsum',
    content:
      'All the Lorem Ipsum generators on the Internet tend to repeat predefined chunks as necessary, making this the first true generator on the Internet.',
  },
  {
    step: 'Stage 3',
    title: 'Lorem Ipsum',
    content:
      'It uses a dictionary of over 200 Latin words, combined with a handful of model sentence structures, to generate Lorem Ipsum which looks reasonable.',
  },
]
</script>
<template>
  <Section variant="secondary">
    <h2 class="text-h2 text-center">Section 2</h2>
    <div class="z-10 mt-10 flex flex-col gap-16 md:mt-13 lg:flex-row">
      <div
        class="flex-1 text-center"
        v-for="(item, index) in section2Items"
        :key="`section2-${index}`"
      >
        <div
          class="relative flex flex-1 flex-col items-center gap-4 sm:gap-8 sm:max-lg:flex-row sm:max-lg:items-start lg:gap-0"
        >
          <!-- 左線 -->
          <div
            v-if="index !== 0 && deviceState.isLg"
            class="absolute top-[66px] z-0 ml-[-250px] h-px w-[calc(50%+64px)] bg-[#404040]"
          ></div>
          <!-- 右線 -->
          <div
            v-if="index !== section2Items.length - 1 && deviceState.isLg"
            class="absolute top-[66px] right-[0] z-0 mr-[-86px] h-px w-[calc(50%+32px)] bg-[#404040]"
          ></div>
          <!-- 中線 -->
          <div
            v-if="index !== section2Items.length - 1 && deviceState.isSm && !deviceState.isLg"
            class="absolute top-[132px] left-[66px] z-0 mr-[-86px] h-[calc(50%+128px)] w-px bg-[#404040]"
          ></div>

          <h4
            class="text-h4 relative z-10 m-auto flex h-33 w-33 flex-shrink-0 items-center justify-center rounded-full bg-[#2E3742] text-white sm:h-33 sm:w-33"
          >
            {{ item.step }}
          </h4>

          <div class="text-center sm:max-lg:text-left lg:mt-8">
            <h4 class="text-h4">{{ item.title }}</h4>
            <p class="text-p2 mt-2 max-w-[400px] sm:max-w-none">{{ item.content }}</p>
          </div>
        </div>
      </div>
    </div>
    <div class="mt-10 flex justify-center">
      <Button variant="primary" text="Button" />
    </div>
  </Section>
</template>
