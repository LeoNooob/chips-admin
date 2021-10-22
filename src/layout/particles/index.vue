<template>
  <div id="particles" />
</template>

<script>
import 'particles.js'
import particlesConfig from '@/assets/particles.json'
export default {
  mounted() {
    window.particlesJS('particles', particlesConfig)
  }
}
</script>

<style lang="scss" scoped>
    @import "@/styles/particles.scss";
</style>
