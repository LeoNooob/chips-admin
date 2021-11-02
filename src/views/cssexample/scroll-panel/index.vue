<template>
  <div class="app-container">
    <div v-for="item in 20" :key="item" class="panel"><h2>{{ item }}</h2></div>
  </div>
</template>

<script>
export default {

}
</script>

<style lang="scss" scoped>
.app-container {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    .panel {
        text-align: center;
        height: 60px;
        width: 80px;
        background-color: orange;
        border: solid;
        border-radius: 4px;
    }
}
</style>
