<template>
  <div class="app-container">
    <div
      class="panel active"
      style="
        background-image: url('https://images.unsplash.com/photo-1615209257690-c8a89ae3edb2?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=2071&q=80');
      "
    >
      <h3>Xiamen</h3>
    </div>
    <div
      class="panel"
      style="
        background-image: url('https://images.unsplash.com/photo-1561560362-647465f3156a?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=1962&q=80');
      "
    >
      <h3>Chengdu</h3>
    </div>
    <div
      class="panel"
      style="
        background-image: url('https://images.unsplash.com/photo-1608709681485-bec9257a3393?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=1974&q=80');
      "
    >
      <h3>Guangzhou</h3>
    </div>
    <div
      class="panel"
      style="
        background-image: url('https://images.unsplash.com/photo-1545268558-b748db4aaf22?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=2070&q=80');
      "
    >
      <h3>Peggys</h3>
    </div>
    <div
      class="panel"
      style="
        background-image: url('https://images.unsplash.com/photo-1529382775970-3f0aca100cef?ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&ixlib=rb-1.2.1&auto=format&fit=crop&w=2070&q=80');
      "
    >
      <h3>Wolfville</h3>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ExpandingCard',
  mounted() {
    const panels = document.querySelectorAll('.panel')

    panels.forEach((panel) => {
      panel.addEventListener('click', () => {
        if (!panel.classList.contains('active')) {
          removeActiveClasses()
          panel.classList.add('active')
        } else {
          window.open('https://baidu.com/', '_blank')
        }
      })
    })

    function removeActiveClasses() {
      panels.forEach((panel) => {
        panel.classList.remove('active')
      })
    }
  }
}
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css?family=Muli&display=swap");

* {
  box-sizing: border-box;
}

body {
  font-family: "Muli", sans-serif;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
  overflow: hidden;
  margin: 0;
}

.app-container {
  display: flex;
  width: 100%;
}

.panel {
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  height: 80vh;
  border-radius: 50px;
  color: #fff;
  cursor: pointer;
  flex: 0.5;
  margin: 10px;
  position: relative;
  transition: all 700ms ease-in;;
  -webkit-transition: all 700ms ease-in;
}

.panel h3 {
  font-size: 24px;
  position: absolute;
  bottom: 20px;
  left: 20px;
  margin: 0;
  opacity: 0;
}

.panel.active {
  flex: 6;
}

.panel.active h3 {
  opacity: 1;
  transition: opacity 0.3s ease-in 0.4s;
}

@media (max-width: 480px) {
  .container {
    width: 100vw;
  }

  .panel:nth-of-type(4),
  .panel:nth-of-type(5) {
    display: none;
  }
}
</style>
