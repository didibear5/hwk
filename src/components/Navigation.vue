<template>
  <div
    class="hide-scrollbar sticky top-0 z-10 mt-[-64px] h-16 w-full overflow-x-auto bg-[#151E1C]/50 text-white sm:px-8 md:px-20 xl:px-40 2xl:px-65"
    :class="[isSticky ? 'bg-opacity-80 fixed top-0 z-50 bg-black backdrop-blur-md' : '']"
  >
    <div class="flex h-full">
      <a
        v-for="(item, index) in navItems"
        :href="`#section${index + 1}`"
        :key="index"
        :ref="(el) => (navRefs[`section${index + 1}`] = el)"
        class="text-p2 relative flex flex-1 cursor-pointer items-center justify-center px-4 whitespace-nowrap"
        :class="[
          activeSection === `section${index + 1}`
            ? `bg-[#151E1C]/80 !font-semibold after:absolute after:bottom-0 after:left-0 after:h-[6px] after:w-full after:bg-[var(--color-primary)] after:content-['']`
            : 'text-white/50 transition hover:text-white',
        ]"
      >
        {{ item }}
      </a>
    </div>
  </div>
</template>

<script setup>
import { ref, watch, inject } from 'vue'

const deviceState = inject('deviceState')

const props = defineProps({
  activeSection: {
    type: String,
    default: 0,
  },
  isSticky: {
    type: Boolean,
    default: false,
  },
})

const activeSection = ref(props.activeSection)
const isSticky = ref(props.isSticky)

const navRefs = ref([])

function debounce(fn, s) {
  let timeId
  return function (...args) {
    clearTimeout(timeId)
    timeId = setTimeout(() => {
      fn(...args)
    }, s)
  }
}
const scrollIntoView = debounce(() => {
  const el = navRefs.value[activeSection.value]
  el.scrollIntoView({ behavior: 'smooth', inline: 'start', block: 'nearest' })
}, 500)

watch(
  () => props.activeSection,
  (newValue) => {
    activeSection.value = newValue
    const el = navRefs.value[newValue]
    if (el && !deviceState.isSm) {
      scrollIntoView()
    }
  },
)

watch(
  () => props.isSticky,
  (newValue) => {
    isSticky.value = newValue
  },
)

const navItems = ['Section 1', 'Section 2', 'Section 3', 'Section 4']
</script>
