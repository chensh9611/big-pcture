<template>
  <div ref="chart13" class="chart">

  </div>
</template>

<script>
import * as echarts from 'echarts'
import {createEchartsOptions} from '@/shared/create-echarts-options.js';
export default {
  name: 'Chart13',
  mounted() {
    const data = [
      {value: 0.08, name: '小程序'},
      {value: 0.06, name: '抖音'},
      {value: 0.11, name: 'PC网页'},
      {value: 0.09, name: '小红书'},
      {value: 0.12, name: '支付宝'},
      {value: 0.06, name: '快手'},
      {value: 0.08, name: 'QQ'},
      {value: 0.08, name: '大众点评'},
    ]
    const myChart = echarts.init(this.$refs.chart13)
    myChart.setOption(createEchartsOptions({
      xAxis: {
        data: data.map(i => i.name),
        axisTick: {show: false},
        axisLine: {
          lineStyle: {color: '#083B70'}
        },
        axisLabel: {
          formatter(val) {
            if (val.length > 2) {
              const array = val.split('');
              array.splice(2, 0, '\n');
              return array.join('');
            } else {
              return val;
            }
          }
        },
      },

      yAxis: {
        splitLine: {show: false},
        axisLine: {
          show: true,
          lineStyle: {color: '#083B70'}
        },
        axisLabel: {
          formatter(value) {
            return (value * 100).toFixed(0) + '%';
          }
        }
      },
      series: [{
        type: 'bar',
        data: data.map(i => i.value),
        color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [{
          offset: 0,
          color: '#0A97FB'
        }, {
          offset: 1,
          color: '#1E34FA'
        }]),
      }]
    }))
  }
}
</script>

<style lang="scss" scoped>

</style>