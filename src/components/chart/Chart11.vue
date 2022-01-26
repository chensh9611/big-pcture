<template>
  <div class="chart11">
    <div class="chart">
      <div class="main" ref="chart11"/>
      </div>
      <div class="legend">
        <span :style="`background: ${colors[0]}`" />上午
        <span :style="`background: ${colors[1]}`" />中午
        <span :style="`background: ${colors[2]}`" />下午
        <span :style="`background: ${colors[3]}`" />晚上
      </div>
    </div>
</template>

<script>
import * as echarts from 'echarts'
import {createEchartsOptions} from '@/shared/create-echarts-options.js';
import {px} from  '@/shared/px.js'
export default {
  name: 'Chart11',
  data(){
    return{
      colors : ['#F46064', '#F38E1C', '#1CDB7C', '#8D70F8', '#33A4FA']
    }
  },
  mounted() {
    const myChart = echarts.init(this.$refs.chart11)
    myChart.setOption(createEchartsOptions({
      color: this.colors,
      xAxis: {show: false},
      yAxis: {show: false},
      legend: {show: false},
      series: [
        {
          startAngle: -20,
          type: 'pie',
          radius: ['25%', '90%'],
          avoidLabelOverlap: false,
          label: {
            show: true, position: 'outside', textStyle: {color: 'white', fontSize: px(20)},
            distanceToLabelLine: 0,
            formatter(options) {
              return options.value * 100 + '%';
            }
          },
          labelLine: {show: true, length: 0},
          roseType: 'area',
          itemStyle: {
            shadowBlur: px(200),
            shadowColor: 'rgba(0, 0, 0, 0.5)'
          },
          data: [
            {value: 0.36, name: '晚上'},
            {value: 0.20, name: '中午'},
            {value: 0.18, name: '上午'},
            {value: 0.24, name: '下午'},
          ]
        }
      ]
    }))
  }
}
</script>

<style lang="scss" scoped>

</style>