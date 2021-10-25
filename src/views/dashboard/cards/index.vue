<template>
  <el-row :gutter="24">
    <div v-for="item in cardGroup" :key="item.title">
      <el-col v-bind="cardGrid" class="el-mb-16">
        <transition name="el-fade-in-linear">
          <el-card v-show="cardShow" shadow="hover" :body-style="item.style">
            <div class="card-content">
              <i :class="item.icon" />
              <div class="card-content-word">
                <div class="card-content-word-title el-m-0 el-p-8">{{ item.title }}</div>
                <div class="card-content-word-value el-m-0 el-p-8 el-fr">{{ item.value }}</div>
              </div>
            </div>
          </el-card>
        </transition>
      </el-col>
    </div>
  </el-row>
</template>

<script>
export default {
  data() {
    return {
      cardGrid: {
        xl: 6,
        lg: 6,
        md: 12,
        sm: 12,
        xs: 24
      },
      cardShow: false,
      cardGroup: [
        { title: '已解决', value: 241, style: 'background: #67C23A; padding: 5px 20px', icon: 'el-icon-question' },
        { title: '待解决', value: 241, style: 'background: #E6A23C; padding: 5px 20px', icon: 'el-icon-check' },
        { title: '驳回', value: 241, style: 'background: #F56C6C; padding: 5px 20px', icon: 'el-icon-error' },
        { title: '超时', value: 241, style: 'background: #409EFF; padding: 5px 20px', icon: 'el-icon-s-flag' }
      ]
    }
  },
  mounted() {
    setTimeout(() => {
      this.cardShow = true
    }, 300)
  }
}
</script>

<style lang="scss" scoped>
.el-card {
    // height: 150px;
    width: 100%;
    .card-content {
        display: flex;
        justify-content: space-between;
        align-items: center;
        i {
            font-size: 3rem;
            color: #FFFFFF;
        }
        &-word {
            color: #FFFFFF;
            &-title {
                font-size: 1.7rem;
                font-weight: bold;
            }
            &-value {
                font-size: 1.7rem;
                font-weight: bold;
            }
        }
    }
}
</style>
