<template>
  <div class="dashboard-container">
    <!-- <div class="dashboard-text">name: {{ name }}</div> -->
    <el-row>
      <el-col :span="8">
        <div>
          <img align="center" :src="urlStats">
        </div>
      </el-col>
      <el-col :span="8">
        <div>
          <img align="center" :src="urlLang">
        </div>
      </el-col>
      <el-col :span="8">
        <div>
          <img align="center" :src="urlWeak">
        </div>
      </el-col>
    </el-row>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'

export default {
  name: 'Dashboard',
  data() {
    return {
      urlStats: 'https://github-readme-stats.vercel.app/api?username=LeoNooob&count_private=true&show_icons=true&theme=flag-india&include_all_commits=true&hide=stars',
      urlLang: 'https://github-readme-stats.vercel.app/api/top-langs?username=LeoNooob&layout=compact',
      urlWeak: 'https://github-readme-stats.vercel.app/api/wakatime?username=LeoNooob'
    }
  },
  computed: {
    ...mapGetters([
      'name'
    ])
  }
}
</script>

<style lang="scss" scoped>
.dashboard {
  &-container {
    margin: 30px;
  }
  &-text {
    font-size: 30px;
    line-height: 46px;
  }
}
</style>
