<script setup>
import Header from './components/Header.vue'
import Navigation from './components/Navigation.vue'
import Section1 from './components/Section1.vue'
import Section2 from './components/Section2.vue'
import Section3 from './components/Section3.vue'
import Section4 from './components/Section4.vue'
import Footer from './components/Footer.vue'
import { ref, reactive, onMounted, onUnmounted, provide } from 'vue'

const sections = ['section1', 'section2', 'section3', 'section4']

const deviceState = reactive({
  isSm: false,
  isMd: false,
  isLg: false,
  isXl: false,
  is2Xl: false,
})
const checkScreen = () => {
  const width = window.innerWidth
  deviceState.isSm = width >= 640
  deviceState.isMd = width >= 768
  deviceState.isLg = width >= 1024
  deviceState.isXl = width >= 1280
  deviceState.is2Xl = width >= 1536
}

const activeSection = ref('section1')
const isSticky = ref(false)
let observer
let headerObserver

onMounted(() => {
  const sectionsSpyRootMargin =
    window.innerHeight > 700 ? `-65px 0px -90% 0px` : `-65px 0px -70% 0px`
  const sectionsSpy = (entries) => {
    entries.forEach((entry) => {
      const { id } = entry.target
      if (!entry.isIntersecting) return
      activeSection.value = id
      history.replaceState(null, '', `#${id}`)
    })
  }
  observer = new IntersectionObserver(sectionsSpy, {
    rootMargin: sectionsSpyRootMargin,
  })
  sections.forEach((section) => {
    const el = document.getElementById(section)
    if (el) observer.observe(el)
  })

  const headerSpy = (entries) => {
    entries.forEach((entry) => {
      isSticky.value = !entry.isIntersecting
    })
  }
  headerObserver = new IntersectionObserver(headerSpy, {
    threshold: 0,
    rootMargin: '-65px 0px 0px 0px',
  })
  const header = document.getElementById('header-section')
  if (header) headerObserver.observe(header)

  checkScreen()
  window.addEventListener('resize', checkScreen)
})

provide('deviceState', deviceState)

onUnmounted(() => {
  if (observer) observer.disconnect()
  if (headerObserver) headerObserver.disconnect()
  window.removeEventListener('resize', checkScreen)
})
</script>

<template>
  <Header id="header-section"></Header>
  <Navigation :activeSection="activeSection" :isSticky="isSticky"></Navigation>
  <Section1 id="section1"></Section1>
  <Section2 id="section2"></Section2>
  <Section3 id="section3"></Section3>
  <Section4 id="section4"></Section4>
  <Footer></Footer>
</template>
