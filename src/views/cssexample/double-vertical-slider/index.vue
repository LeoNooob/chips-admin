<template>
  <div class="slider-container">
    <div class="left-slide">
      <div style="background-color: #6495ED;">
        <vue-typed-js v-if="activeSlideIndex === 3" :strings="['Greenwood<br/>September 3, 2017']" :cursor-char="'_'" :content-type="'html'">
          <h1 class="typing" />
        </vue-typed-js>
      </div>
      <div style="background-color: #B16347;">
        <vue-typed-js v-if="activeSlideIndex === 2" :strings="['Wolfville<br/>June 26, 2018']" :cursor-char="'_'" :content-type="'html'">
          <h1 class="typing" />
        </vue-typed-js>
      </div>
      <div style="background-color: #2A86BA;">
        <vue-typed-js v-if="activeSlideIndex === 1" :strings="['Peggys<br/>December 20, 2019']" :cursor-char="'_'" :content-type="'html'">
          <h1 class="typing" />
        </vue-typed-js>
      </div>
      <div style="background-color: #FFB866;">
        <vue-typed-js v-if="activeSlideIndex === 0" :strings="['Guangzhou<br/>December 23, 2020']" :cursor-char="'_'" :content-type="'html'">
          <h1 class="typing" />
        </vue-typed-js>
      </div>
    </div>
    <div class="right-slide">
      <div style="background-image: url('https://images.unsplash.com/photo-1608709681485-bec9257a3393?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=1974&q=80');" />
      <div style="background-image: url('https://images.unsplash.com/photo-1545268558-b748db4aaf22?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=2070&q=80');" />
      <div style="background-image: url('https://images.unsplash.com/photo-1561560362-339e2f14a7de?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=1474&q=80');" />
      <div style="background-image: url('https://images.unsplash.com/photo-1504371311804-ca5cc55e57a8?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1470&q=80');" />
    </div>
    <div class="action-buttons">
      <button class="down-button">
        <i class="el-icon-caret-bottom" />
      </button>
      <button class="up-button">
        <i class="el-icon-caret-top" />
      </button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      activeSlideIndex: 0,
      list: [
        { index: 0, color: '#FFB866', location: 'Guangzhou', date: 'December 23, 2020', url: 'https://images.unsplash.com/photo-1608709681485-bec9257a3393?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=1974&q=80' },
        { index: 1, color: '#2A86BA', location: 'Peggys', date: 'December 20, 2019', url: 'https://images.unsplash.com/photo-1545268558-b748db4aaf22?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=2070&q=80' },
        { index: 2, color: '#B16347', location: 'Wolfville', date: 'June 26, 2018', url: 'https://images.unsplash.com/photo-1561560362-339e2f14a7de?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=1474&q=80' },
        { index: 3, color: '#FFB866', location: 'Greenwood', date: 'September 3, 2017', url: 'https://images.unsplash.com/photo-1504371311804-ca5cc55e57a8?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1470&q=80' }
      ]
    }
  },
  mounted() {
    const sliderContainer = document.querySelector('.slider-container')
    const slideRight = document.querySelector('.right-slide')
    const slideLeft = document.querySelector('.left-slide')
    const upButton = document.querySelector('.up-button')
    const downButton = document.querySelector('.down-button')
    const slidesLength = slideRight.querySelectorAll('div').length

    const that = this

    slideLeft.style.top = `-${(slidesLength - 1) * 100}vh`

    upButton.addEventListener('click', () => changeSlide('up'))
    downButton.addEventListener('click', () => changeSlide('down'))

    const changeSlide = (direction) => {
      const sliderHeight = sliderContainer.clientHeight
      if (direction === 'up') {
        that.activeSlideIndex++
        if (that.activeSlideIndex > slidesLength - 1) {
          that.activeSlideIndex = 0
        }
      } else if (direction === 'down') {
        that.activeSlideIndex--
        if (that.activeSlideIndex < 0) {
          that.activeSlideIndex = slidesLength - 1
        }
      }

      slideRight.style.transform = `translateY(-${that.activeSlideIndex * sliderHeight}px)`
      slideLeft.style.transform = `translateY(${that.activeSlideIndex * sliderHeight}px)`
    }
  }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css?family=Open+Sans');

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Open Sans', sans-serif;
  height: 100vh;
}

.slider-container {
  position: relative;
  overflow: hidden;
  width: 100%;
  height: 100vh;
}

.left-slide {
  height: 100%;
  width: 35%;
  position: absolute;
  top: 0;
  left: 0;
  transition: transform 0.5s ease-in-out;
}

.left-slide > div {
  height: 100%;
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  color: #fff;
}

.left-slide h1 {
  font-size: 40px;
  margin-bottom: 10px;
  margin-top: -30px;
}

.right-slide {
  height: 100%;
  position: absolute;
  top: 0;
  left: 35%;
  width: 65%;
  transition: transform 0.5s ease-in-out;
}

.right-slide > div {
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center center;
  height: 100%;
  width: 100%;
}

button {
  background-color: #fff;
  border: none;
  color: #aaa;
  cursor: pointer;
  font-size: 16px;
  padding: 15px;
}

button:hover {
  color: #222;
}

button:focus {
  outline: none;
}

.slider-container .action-buttons button {
  position: absolute;
  left: 35%;
  top: 50%;
  z-index: 100;
}

.slider-container .action-buttons .down-button {
  transform: translateX(-100%);
  border-top-left-radius: 5px;
  border-bottom-left-radius: 5px;
}

.slider-container .action-buttons .up-button {
  transform: translateY(-100%);
  border-top-right-radius: 5px;
  border-bottom-right-radius: 5px;
}

</style>
