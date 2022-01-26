<template>
  <div class="年龄段-图3">
    <h3>消费者年龄趋势图</h3>
    <div ref="charts9" class="chart">

    </div>
  </div>
</template>

<script>
import * as echarts from 'echarts'
import {createEchartsOptions} from '@/shared/create-echarts-options.js';
import {px} from  '@/shared/px.js'
export default {
  name: 'Chart9',
  mounted() {
    const myChart = echarts.init(this.$refs.charts9);
    myChart.setOption(createEchartsOptions({
      color: '#F7A110',
      xAxis: {
        type: 'category',
        boundaryGap: false,
        data: [0, 18, 25, 32, 40, 50, 60,70],
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
      series: [{
        type: 'line',
        data: [
          0.10, 0.15, 0.26,
          0.12, 0.09, 0.06,
          0.02,
        ],
        symbol: 'circle',
        symbolSize: px(12),
        lineStyle: {width: px(2)},
        areaStyle: {
          color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [{
            offset: 0,
            color: '#F7A110'
          }, {
            offset: 1,
            color: '#1B1D52'
          }]),
        }
      }]
    }));
  }
}
</script>

<style lang="scss" scoped>

</style>