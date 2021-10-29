<template>
  <div class="app-container">
    <section class="bg" />
    <div class="loading-text">{{ loading }}%</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      loading: 0
    }
  },
  mounted() {
    const loadText = document.querySelector('.loading-text')
    const bg = document.querySelector('.bg')

    const int = setInterval(blurring, 30)

    const that = this
    function blurring() {
      that.loading++

      if (that.loading > 99) {
        clearInterval(int)
      }

      loadText.style.opacity = scale(that.loading, 0, 100, 1, 0)
      bg.style.filter = `blur(${scale(that.loading, 0, 100, 30, 0)}px)`
    }

    // https://stackoverflow.com/questions/10756313/javascript-jquery-map-a-range-of-numbers-to-another-range-of-numbers
    const scale = (num, in_min, in_max, out_min, out_max) => {
      return ((num - in_min) * (out_max - out_min)) / (in_max - in_min) + out_min
    }
  }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css?family=Ubuntu');

* {
  box-sizing: border-box;
}

.app-container {
  font-family: 'Ubuntu', sans-serif;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 94.8vh;
  overflow: hidden;
  margin: 0;
}

.bg {
  background: url('https://images.unsplash.com/photo-1545268558-b748db4aaf22?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=1470&q=80')
    no-repeat center center/cover;
  position: absolute;
  top: -30px;
  left: -30px;
  width: calc(100vw + 60px);
  height: calc(100vh + 60px);
  z-index: -1;
  filter: blur(0px);
}

.loading-text {
  font-size: 50px;
  color: #fff;
}

</style>
