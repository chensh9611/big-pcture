<template>
  <div class="bordered 管辖统计">
    <h2>直营店统计</h2>
    <div ref="charts1" class="chart">

    </div>
  </div>
</template>

<script>
import * as echarts from 'echarts'
import {createEchartsOptions} from '@/shared/create-echarts-options.js';
export default {
  name: 'Chart1',
  mounted() {
    const myChart = echarts.init(this.$refs.charts1)
    myChart.setOption(createEchartsOptions({
      xAxis: {
        data: ['上海市', '北京市', '浙江省', '湖南省', '江苏省', '四川省', '湖北省', '江西省', '河北省'],
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
        }
      },
      series: [{
        type: 'bar',
        data: [10, 20, 36, 41, 15, 26, 37, 18, 29]
      }]
    }));
  }
}
</script>

<style lang="scss" scoped>
</style>