<template>
  <div class="bordered 发案趋势">
    <h2>渠道分析</h2>
    <div ref="charts3" class="chart"/>
  </div>
</template>

<script>
import * as echarts from 'echarts'
import {createEchartsOptions} from '@/shared/create-echarts-options.js';
import {px} from  '@/shared/px.js'
export default {
  name: 'Chart3',
  mounted() {
    const myChart = echarts.init(this.$refs.charts3)
    myChart.setOption(createEchartsOptions({
      legend: {
        bottom: px(10),
        textStyle: {color: 'white'},
        itemWidth: px(30),
        itemHeight: px(16)
      },
      grid: {
        x: px(20),
        x2: px(20),
        y: px(20),
        y2: px(70),
        containLabel: true
      },
      xAxis: {
        type: 'category',
        boundaryGap: false,
        data: [2013, 2014, 2015, 2016, 2017, 2018, 2019, 2020, 2021],
        splitLine: {show: true, lineStyle: {color: '#073E78'}},
        axisTick: {show: false},
        axisLine: {show: false},
      },
      yAxis: {
        type: 'value',
        splitLine: {lineStyle: {color: '#073E78'}},
        axisLabel: {
          formatter(val) {
            return val * 100 + '%';
          }
        }
      },
      series: [
        {
          name: '手机软件',
          type: 'line',
          data: [0.01, 0.02, 0.03, 0.04, 0.05, 0.06, 0.07, 0.08, 0.09]
        },
        {
          name: 'PC网页',
          type: 'line',
          data: [0.02, 0.03, 0.04, 0.05, 0.06, 0.07, 0.08, 0.09, 0.10].reverse()
        },
        {
          name: '小程序',
          type: 'line',
          data: [0.00, 0.00, 0.00, 0.07, 0.08, 0.09, 0.09, 0.12, 0.13]
        },
        {
          name: '线下直营',
          type: 'line',
          data: [0.04, 0.05, 0.06, 0.07, 0.08, 0.09, 0.10, 0.11, 0.12].reverse()
        },
      ].map(obj => ({
        ...obj,
        symbol: 'circle',
        symbolSize: px(12),
        lineStyle: {width: px(2)}
      }))
    }));
  }
}
</script>

<style lang="scss" scoped>

</style>