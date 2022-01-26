<template>
  <div class="年龄段-图1">
    <div class="chart">
      <div class="main" ref="charts7"/>
        <div class="text">性别</div>
      </div>
      <div class="legend">
        <span class="male"/>男
        <span class="female"/>女
      </div>
    </div>
</template>

<script>
import * as echarts from 'echarts'
import {createEchartsOptions} from '@/shared/create-echarts-options.js';
import {px} from  '@/shared/px.js'
export default {
  name: 'Chart7',
  mounted() {
    const myChart = echarts.init(this.$refs.charts7)
    myChart.setOption(createEchartsOptions({
      color: ['#8D70F8', '#33A4FA'],
      xAxis: {show: false},
      yAxis: {show: false},
      legend: {show: false},
      series: [
        {
          name: '访问来源',
          type: 'pie',
          radius: ['75%', '90%'],
          avoidLabelOverlap: false,
          label: {
            show: true, position: 'inside', textStyle: {color: 'white', fontSize: px(20)},
            formatter(options) {
              return options.value * 100 + '%';
            }
          },
          labelLine: {show: false},
          itemStyle: {
            borderColor: '#0F113A',
            borderWidth: px(4)
          },
          data: [
            {value: 0.4, name: '男'},
            {value: 0.6, name: '女'},
          ]
        }
      ]
    }));
  }
}
</script>

<style lang="scss" scoped>

</style>