<template>
  <div class="bordered 籍贯">
    <h2>购物排行前五地区</h2>
    <div class="wrapper">
      <div ref="charts6" class="chart"/>
      <div class="legend bordered">
        <span class="icon" :style="`background: ${colors.上海市}`"/>上海市
        <span class="icon" :style="`background: ${colors.北京市}`"/>北京市
        <span class="icon" :style="`background: ${colors.浙江省}`"/>浙江省
        <span class="icon" :style="`background: ${colors.四川省}`"/>四川省
        <span class="icon" :style="`background: ${colors.湖南省}`"/>湖南省
      </div>
      <div class="notes">此地图仅显示了中国的部分区域</div>
    </div>
  </div>
</template>

<script>
import * as echarts from 'echarts'
import {createEchartsOptions} from '@/shared/create-echarts-options.js';
import china from '@/geo/china.json';
export default {
  name: 'Chart6',
  data(){
    return {
      colors: {'上海市': '#BB31F7', '北京市': '#15B8FD', '浙江省': '#06E1EE', '四川省':'#FFFDDE', '湖南省':'#D9D7F1'}
    }
  },
  mounted() {
    const myChart = echarts.init(this.$refs.charts6)
    echarts.registerMap('CN', china);
    myChart.setOption(createEchartsOptions({
      xAxis: {show: false},
      yAxis: {show: false},
      series: [
        {
          type: 'map',
          mapType: 'CN', // 自定义扩展图表类型
          data: [
            {name: '上海市', value: 1},
          ],
          label: {show: false, color: 'white'},
          itemStyle: {
            areaColor: '#010D3D',
            color: this.colors.上海市,
            borderColor: '#01A7F7',
            emphasis: {
              label: {color: 'white'},
              areaColor: '#5470C6',
            },
          }
        },
        {
          type: 'map',
          mapType: 'CN', // 自定义扩展图表类型
          data: [
            {name: '北京市', value: 100},
          ],
          itemStyle: {
            areaColor: '#010D3D',
            color: this.colors.北京市,
            borderColor: 'yellow',
            emphasis: {
              label: {color: 'white'},
              areaColor: '#5470C6',
            },
          }
        },
        {
          type: 'map',
          mapType: 'CN', // 自定义扩展图表类型
          data: [
            {name: '浙江省', value: 100},
          ],
          itemStyle: {
            areaColor: '#010D3D',
            color: this.colors.浙江省,
            borderColor: '#01A7F7',
            emphasis: {
              label: {color: 'white'},
              areaColor: '#5470C6',
            },
          }
        },
        {
          type: 'map',
          mapType: 'CN', // 自定义扩展图表类型
          data: [
            {name: '湖南省', value: 100},
          ],
          itemStyle: {
            areaColor: '#010D3D',
            color: this.colors.湖南省,
            borderColor: '#01A7F7',
            emphasis: {
              label: {color: 'white'},
              areaColor: '#5470C6',
            },
          }
        },
        {
          type: 'map',
          mapType: 'CN', // 自定义扩展图表类型
          data: [
            {name: '四川省', value: 100},
          ],
          itemStyle: {
            areaColor: '#010D3D',
            color: this.colors.四川省,
            borderColor: '#01A7F7',
            emphasis: {
              label: {color: 'white'},
              areaColor: '#5470C6',
            },
          }
        },

      ]
    }));
  }
}
</script>

<style lang="scss" scoped>

</style>