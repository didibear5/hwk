<script setup>
defineProps({
  variant: {
    type: String,
    default: 'primary',
    validator: (value) => ['primary', 'outline'].includes(value),
  },
  text: {
    type: String,
    default: 'Button',
  },
})
</script>

<template>
  <button
    :class="[
      variant === 'primary'
        ? 'bg-[var(--color-primary)] text-white hover:bg-[var(--color-primary)]'
        : 'border border-[#2789F2] text-[#2789F2] hover:border-[var(--color-primary)] hover:bg-[var(--color-primary)] hover:text-white',
      'h-[46px] min-w-30 cursor-pointer rounded-full text-base/6 font-normal transition',
    ]"
  >
    {{ text }}
  </button>
</template>
