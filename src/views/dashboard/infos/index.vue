<template>
  <el-row :gutter="24">
    <el-col v-bind="grid" class="el-mb-16">
      <transition name="el-fade-in-linear">
        <el-card v-show="show" :body-style="{padding: '0px'}">
          <div class="info-content">
            <img align="center" :src="urlStats" loading="lazy">
          </div>
        </el-card>
      </transition>
    </el-col>
    <el-col v-bind="grid" class="el-mb-16">
      <transition name="el-fade-in-linear">
        <el-card v-show="show" :body-style="{padding: '0px'}">
          <div class="info-content">
            <img align="center" :src="urlLang" loading="lazy">
          </div>
        </el-card>
      </transition>
    </el-col>
  </el-row>
</template>

<script>
export default {
  data() {
    return {
      grid: {
        xl: 12,
        lg: 12,
        md: 12,
        sm: 24,
        xs: 25
      },
      urlStats: 'https://github-readme-stats.vercel.app/api?username=LeoNooob&count_private=true&show_icons=true&theme=flag-india&include_all_commits=true&hide=stars&hide_border=true',
      urlLang: 'https://github-readme-stats.vercel.app/api/top-langs?username=LeoNooob&layout=compact&hide_border=true',
      show: false
    }
  },
  mounted() {
    setTimeout(() => {
      this.show = true
    }, 300)
  }
}
</script>

<style lang="scss" scoped>
.info {
    &-content {
        height: 210px;
        display: flex;
        justify-content: center;
        align-items: center;
    }
}
</style>
