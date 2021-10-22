
<script>
import 'particles.js'
import particlesConfig from '@/assets/particles.json'
export default {
  mounted() {
    window.particlesJS('particles', particlesConfig)
  },
  render(h) {
    return <div id='particles'></div>
  }
}
</script>

<style lang="scss" scoped>
    @import "@/styles/particles.scss";
</style>
