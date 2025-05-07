<script setup>
const footerItems = ['Terms & Conditions', 'Privacy', 'Cookie Preference']
</script>
<template>
  <footer
    class="text-p3 flex flex-col justify-center bg-black px-4 py-5 text-white sm:px-8 md:px-20 lg:flex-row lg:max-xl:justify-between xl:items-center"
  >
    <div class="flex flex-col items-start xl:flex-row xl:items-center">
      <img
        src="/logo_white.svg"
        alt="Synology Logo"
        class="mr-9 h-9 border-0 pr-9 xl:inline-block xl:border-r-1"
      />
      <span class="mt-2 xl:mt-0">Copyright © 2025 Synology Inc. All rights reserved.</span>
    </div>
    <div class="mt-2 flex flex-col sm:flex-row lg:items-end xl:mt-0 xl:ml-6">
      <span
        v-for="(item, index) in footerItems"
        :key="`footerItems-${index}`"
        class="border-0 pr-2 sm:mr-2 sm:border-r-1"
      >
        <a class="cursor-pointer">{{ item }}</a>
      </span>
      <span class="flex cursor-pointer items-center">
        <img src="/earth.svg" alt="Synology Logo" class="w-[22px]" />
        <span> Global - English </span>
      </span>
    </div>
  </footer>
</template>
