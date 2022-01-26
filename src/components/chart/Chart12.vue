<template>
  <div class="chart12">
    <div class="chart">
      <div class="main" ref="chart12"/>
      </div>
    </div>
</template>

<script>
import * as echarts from 'echarts'
import {createEchartsOptions} from '@/shared/create-echarts-options.js';
import {px} from  '@/shared/px.js'
export default {
  name: 'Chart12',
  mounted() {
    const data = [
      {value: 0.08, name: '耐克'},
      {value: 0.06, name: '阿迪达斯'},
      {value: 0.11, name: '华为'},
      {value: 0.09, name: 'Apple'},
      {value: 0.12, name: '特斯拉'},
      {value: 0.06, name: '荣耀'},
      {value: 0.08, name: '小米'},
      {value: 0.08, name: '道道全'},
      {value: 0.08, name: '哇哈哈'},
    ];
    const myChart = echarts.init(this.$refs.chart12)
    myChart.setOption(createEchartsOptions({
      xAxis: {show: false},
      yAxis: {show: false},
      grid: {x: 0, x2: 0, y: 0, y2: 0, containLabel: true},
      legend: {
        orient: 'vertical',
        left: 'left',
        top: 'center',
        textStyle: {color: 'white'},
        itemWidth: px(10),
        itemHeight: px(10),
        formatter(name) {
          const value = data.find(i => i.name === name)?.value * 100 + '%';
          return name + ' ' + value;
        }
      },
      series: [
        {
          center: ['60%', '50%'],
          type: 'pie',
          radius: '80%',
          label: {show: false},
          labelLine: {show: false},
          data: data,
          emphasis: {
            itemStyle: {
              shadowBlur: 10,
              shadowOffsetX: 0,
              shadowColor: 'rgba(0, 0, 0, 0.5)'
            }
          }
        }
      ]
    }))
  }
}
</script>

<style lang="scss" scoped>

</style>