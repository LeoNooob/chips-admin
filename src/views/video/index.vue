<template>
  <div class="app-container">
    <video ref="vdom" controls width="100%" height="600" class="el-p-16" />
  </div>
</template>

<script>
import flvjs from 'flv.js'
export default {
  name: 'Video',
  props: {
    // msg: String
  },
  mounted() {
    this.$nextTick(() => {
      this.createVideo()
    })
  },
  methods: {
    createVideo() {
      if (flvjs.isSupported()) {
        var ve = this.$refs.vdom
        var flvplayer = flvjs.createPlayer({
          type: 'flv',
          url: 'http://example.com/flv/video.flv'
        })
        flvplayer.attachMediaElement(ve)
        flvplayer.load()
        flvplayer.play()
      }
    }
  }
}
</script>

<style>

</style>
