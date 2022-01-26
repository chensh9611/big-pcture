<template>
  <div ref="charts10" class="chart"></div>
</template>

<script>
import * as echarts from 'echarts'
import {createEchartsOptions} from '@/shared/create-echarts-options.js';
export default {
  name: 'Chart10',
  mounted() {
    const myChart = echarts.init(this.$refs.charts10);
    myChart.setOption(createEchartsOptions({
      xAxis: {
        data: ['女装', '美妆护肤', '手机', '母婴童装', '医疗保健'],
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
        data: [40, 22, 20, 18, 32],
        color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [{
          offset: 0,
          color: '#0A97FB'
        }, {
          offset: 1,
          color: '#1E34FA'
        }]),
      }]
    }));
  }
}
</script>

<style lang="scss" scoped>

</style>