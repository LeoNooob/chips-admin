<template>
  <div class="dashboard-container">
    <!-- <div class="dashboard-text">name: {{ name }}</div> -->
    <div class="dashbord-cards">
      <card-group />
    </div>
    <div class="dashbord-mine">
      <info-group />
    </div>
    <div class="dashbord-chart">
      <chart-group ref="chart" />
    </div>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
import CardGroup from './cards'
import InfoGroup from './infos'
import ChartGroup from './charts'

export default {
  name: 'Dashboard',
  components: { CardGroup, InfoGroup, ChartGroup },
  data() {
    return {
    }
  },
  computed: {
    ...mapGetters([
      'name'
    ])
  },
  mounted() {
  },
  beforeDestroy() {
  }
}
</script>

<style lang="scss" scoped>
.dashboard {
  &-container {
    margin: 30px;

  }
  &-text {
    line-height: 46px;
  }
}
</style>
