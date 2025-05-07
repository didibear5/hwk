<script setup>
defineProps({
  variant: {
    type: String,
    default: 'primary',
    validator: (value) => ['primary', 'secondary'].includes(value),
  },
})
</script>

<template>
  <div
    class="w-full scroll-mt-16 px-4 py-10 sm:px-8 sm:py-13 md:px-20 lg:py-25 xl:px-40 2xl:px-65"
    :class="[variant === 'secondary' ? 'bg-[#E6E6E6]/50' : '']"
  >
    <slot></slot>
  </div>
</template>
