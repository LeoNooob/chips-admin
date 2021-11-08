<template>
  <div class="app-container">
    <div class="search">
      <input v-model="searchword" type="text" class="input" placeholder="搜索...">
      <button class="btn">
        <i class="el-icon-search" />
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HiddenSearch',
  data() {
    return {
      searchword: ''
    }
  },
  mounted() {
    const search = document.querySelector('.search')
    const btn = document.querySelector('.btn')
    const input = document.querySelector('.input')

    const that = this

    btn.addEventListener('click', () => {
      if (search.classList.contains('active') && that.searchword !== '') {
        that.search(that.searchword)
      } else {
        search.classList.toggle('active')
        input.focus()
      }
    })
  },
  methods: {
    search(wd) {
      this.$message(wd)
    }
  }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

* {
  box-sizing: border-box;
}

.app-container {
  background-image: linear-gradient(90deg, #7d5fff, #7158e2);
  font-family: 'Roboto', sans-serif;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 94.5vh;
  overflow: hidden;
  margin: 0;
}

.search {
  position: relative;
  height: 50px;
}

.search .input {
  background-color: #fff;
  border: 0;
  font-size: 18px;
  padding: 15px;
  height: 50px;
  width: 50px;
  transition: width 0.3s ease;
}

.btn {
  background-color: #fff;
  border: 0;
  cursor: pointer;
  font-size: 24px;
  position: absolute;
  top: 0;
  left: 0;
  height: 50px;
  width: 50px;
  transition: transform 0.3s ease;
}

.btn:focus,
.input:focus {
  outline: none;
}

.search.active .input {
  width: 200px;
}

.search.active .btn {
  transform: translateX(198px);
}

</style>
