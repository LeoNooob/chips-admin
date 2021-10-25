<template>
  <div>
    <el-row :gutter="24">
      <el-col v-bind="grid" class="el-mb-16">
        <div ref="bar" class="chart" />
      </el-col>
      <el-col v-bind="grid" class="el-mb-16">
        <div ref="pie" class="chart" />
      </el-col>
      <el-col v-bind="grid" class="el-mb-16">
        <div ref="radar" class="chart" />
      </el-col>
      <el-col :span="24" class="el-mb-16">
        <div ref="hot" class="chart" />
      </el-col>
    </el-row>
  </div>
</template>

<script>
import * as echarts from 'echarts'
export default {
  data() {
    return {
      grid: {
        xl: 8,
        lg: 8,
        md: 8,
        sm: 24,
        xs: 24
      }
    }
  },
  mounted() {
    this.initChart()
    const that = this
    window.onresize = () => {
      that.refresh()
    }
  },
  beforeDestroy() {
    window.onresize = null
  },
  methods: {
    refresh() {
      if (this.barChart !== undefined) {
        this.barChart.resize()
        this.pieChart.resize()
        this.radarChart.resize()
        this.hotChart.resize()
      }
    },
    initChart() {
      this.barChart = echarts.init(this.$refs.bar)
      this.barChart.setOption({
        xAxis: {
          type: 'value'
        },
        yAxis: {
          type: 'category',
          data: ['1', '2', '3', '4', '5']
        },
        legend: {
          data: ['合格']
        },
        series: [
          {
            name: '合格',
            data: [135, 164, 150, 160, 145],
            type: 'bar',
            stack: '总量',
            smooth: true,
            label: {
              show: true,
              position: 'top'
            }
          }
        ]
      })
      this.pieChart = echarts.init(this.$refs.pie)
      this.pieChart.setOption({
        title: {
          text: '',
          left: 'center'
        },
        tooltip: {
          trigger: 'item',
          formatter: '{a} <br/>{b} : {c} ({d}%)'
        },
        legend: {
          left: 'center',
          top: 'bottom',
          data: [
            'rose1',
            'rose2',
            'rose3',
            'rose4',
            'rose5'
          ]
        },
        series: [
          {
            name: 'Radius Mode',
            type: 'pie',
            radius: [20, 140],
            roseType: 'radius',
            itemStyle: {
              borderRadius: 5
            },
            label: {
              show: false
            },
            emphasis: {
              label: {
                show: true
              }
            },
            data: [
              { value: 40, name: 'rose1' },
              { value: 33, name: 'rose2' },
              { value: 28, name: 'rose3' },
              { value: 22, name: 'rose4' },
              { value: 20, name: 'rose5' }
            ]
          }
        ]
      })
      this.radarChart = echarts.init(this.$refs.radar)
      this.radarChart.setOption({
        legend: {
          data: ['Allocated Budget', 'Actual Spending']
        },
        radar: {
          // shape: 'circle',
          indicator: [
            { name: 'Sales', max: 6500 },
            { name: 'Administration', max: 16000 },
            { name: 'IT', max: 30000 },
            { name: 'Customer Supp.', max: 38000 },
            { name: 'Development', max: 52000 },
            { name: 'Marketing', max: 25000 }
          ]
        },
        series: [
          {
            name: 'Budget vs spending',
            type: 'radar',
            data: [
              {
                value: [4200, 3000, 20000, 35000, 50000, 18000],
                name: 'Allocated Budget'
              },
              {
                value: [5000, 14000, 28000, 26000, 42000, 21000],
                name: 'Actual Spending'
              }
            ]
          }
        ]
      })
      this.hotChart = echarts.init(this.$refs.hot)
      this.hotChart.setOption({
        title: {
          top: 30,
          left: 'center',
          text: 'Daily Step Count'
        },
        tooltip: {},
        visualMap: {
          min: 0,
          max: 10000,
          type: 'piecewise',
          orient: 'horizontal',
          left: 'center',
          top: 65
        },
        calendar: {
          top: 120,
          left: 30,
          right: 30,
          cellSize: ['auto', 40],
          range: '2016',
          itemStyle: {
            borderWidth: 0.5
          },
          yearLabel: { show: false }
        },
        series: {
          type: 'heatmap',
          coordinateSystem: 'calendar',
          data: this.getVirtulData('2016')
        }
      })
    },
    getVirtulData(year) {
      year = year || '2017'
      var date = +echarts.number.parseDate(year + '-01-01')
      var end = +echarts.number.parseDate(+year + 1 + '-01-01')
      var dayTime = 3600 * 24 * 1000
      var data = []
      for (var time = date; time < end; time += dayTime) {
        data.push([
          echarts.format.formatTime('yyyy-MM-dd', time),
          Math.floor(Math.random() * 10000)
        ])
      }
      return data
    }
  }
}
</script>

<style lang="scss" scoped>
.chart {
    height: 450px;
    background: white;
    justify-content: center;
    align-items: center;
}
</style>
