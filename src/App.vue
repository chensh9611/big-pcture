<template>
  <div id="root" style="color: white">
    <div id="app">
      <Home/>
    </div>
  </div>
</template>

<script>
import Home from '@/components/Home.vue'
const clientWidth = document.documentElement.clientWidth
const clientHeight = document.documentElement.clientHeight
const pageWidth = clientWidth / clientHeight > 16 / 9 ? clientHeight * (16 / 9) : clientWidth
window.pageWidth = pageWidth
const pageHeight = pageWidth / (16 / 9)
const string = `<style>html{
      font-size: ${pageWidth / 100}px
    }</style>`
document.write(string)
const root = document.querySelector('#root')
console.log(root)
root.style.height = pageHeight + 'px'
root.style.marginTop = (clientHeight - pageHeight) / 2 + 'px'
export default {
  name: 'App',
  components: {
    Home

  },
  mounted() {
    const root = document.querySelector('#app')
    console.log(root)
    root.style.height = pageHeight + 'px'
    root.style.marginTop = (clientHeight - pageHeight) / 2 + 'px'
  }
}
</script>

<style>
</style>
