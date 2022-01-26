<template>
  <div class="bordered 破获排名">
    <h2>直营门店排名</h2>
    <div ref="charts2" class="chart"/>
    <div class="legend">
      <span class="first"/> 销量排名
      <span class="second"/> 销售额排名
    </div>
  </div>
</template>

<script>
import * as echarts from 'echarts'
import {createEchartsOptions} from '@/shared/create-echarts-options.js';
export default {
  name: 'Chart2',
  data() {
    return {
      myChart: null
    }
  },
  mounted() {
    this.myChart = echarts.init(this.$refs.charts2)
    const data = [
      {name: '上海市', 2011: 2, 2012: 3},
      {name: '北京市', 2011: 2, 2012: 3},
      {name: '浙江省', 2011: 2, 2012: 3},
      {name: '湖南省', 2011: 2, 2012: 3},
      {name: '江苏省', 2011: 2, 2012: 3},
      {name: '四川省', 2011: 2, 2012: 3},
      {name: '湖北省', 2011: 2, 2012: 3},
      {name: '江西省', 2011: 2, 2012: 3},
      {name: '河北省', 2011: 2, 2012: 3},
    ];
    setInterval(() => {
      const newData = [
        {name: '上海市', 2011: 2, 2012: Math.random() * 10},
        {name: '北京市', 2011: 2, 2012: 3},
        {name: '浙江省', 2011: 2, 2012: 3},
        {name: '湖南省', 2011: 2, 2012: 3},
        {name: '江苏省', 2011: 2, 2012: 3},
        {name: '四川省', 2011: 2, 2012: 3},
        {name: '湖北省', 2011: 2, 2012: 3},
        {name: '江西省', 2011: 2, 2012: 3},
        {name: '河北省', 2011: 2, 2012: 3},
      ];
      x(newData);
    }, 1000);
    const x = (data) => {
      this.myChart.current.setOption(createEchartsOptions({
        xAxis: {
          type: 'value',
          boundaryGap: [0, 0.01],
          splitLine: {show: false},
          axisLabel: {show: false}
        },
        yAxis: {
          axisTick: {show: false},
          type: 'category',
          data: data.map(i => i.name),
          axisLabel: {
            formatter(val) {
              return val.replace('公安局', '\n公安局');
            }
          }
        },
        series: [
          {
            name: '2011年',
            type: 'bar',
            data: data.map(i => i[2011]),
            itemStyle: {
              normal: {
                color: new echarts.graphic.LinearGradient(0, 0, 1, 0, [{
                  offset: 0,
                  color: '#2034F9'
                }, {
                  offset: 1,
                  color: '#04A1FF'
                }]),
              }
            }
          },
          {
            name: '2012年',
            type: 'bar',
            data: data.map(i => i[2012]),
            itemStyle: {
              normal: {
                color: new echarts.graphic.LinearGradient(0, 0, 1, 0, [{
                  offset: 0,
                  color: '#B92AE8'
                }, {
                  offset: 1,
                  color: '#6773E7'
                }]),
              }
            }
          }
        ]
      }));

    };
    this.myChart.current = echarts.init(this.$refs.charts2);
    x(data);
  }
}
</script>

<style lang="scss" scoped>

</style>