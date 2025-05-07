<script setup>
import Button from './Button.vue'
</script>
<template>
  <header class="relative w-full sm:h-[500px] sm:bg-black lg:h-[600px] xl:h-[666px]">
    <div
      class="z-1 h-full w-full bg-black/60 px-4 pt-10 pb-30 text-white sm:absolute sm:px-8 md:px-20 lg:bottom-0 lg:w-auto lg:bg-transparent lg:bg-[linear-gradient(to_right,black_60%,transparent)] lg:pt-25 lg:pr-25 lg:pb-0 xl:pl-40 2xl:pl-65"
    >
      <img src="/logo_white.svg" alt="Synology Logo" class="h-9" />
      <h1 class="text-h1 mt-10">What is Lorem Ipsum?</h1>
      <p class="text-p1 mt-4 max-w-[600px]">
        Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has
        been the industry's standard dummy text ever since the 1500s, when an unknown printer took a
        galley of type and scrambled it to make a type specimen book.
      </p>
      <div class="mt-8 flex flex-col gap-5 min-[300px]:flex-row">
        <Button variant="primary" text="Button" />
        <Button variant="outline" text="Button" />
      </div>
    </div>
    <img
      src="/img_banner.jpg"
      srcset="/img_banner.jpg 1x, /img_banner@2x.jpg 2x"
      alt="Server"
      class="absolute top-0 right-0 bottom-0 left-0 z-[-1] h-full w-full object-cover sm:z-0 lg:left-auto lg:max-xl:w-3/5 xl:w-auto"
    />
  </header>
</template>
