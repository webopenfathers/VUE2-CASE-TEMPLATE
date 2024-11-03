<template>
  <div class="box" ref="graphRef"></div>
</template>

<script>
import * as echarts from 'echarts'
export default {
  name: 'graphChart',
  data() {
    return {}
  },
  mounted() {
    this.renderChart()
  },
  methods: {
    renderChart() {
      // 基于准备好的dom，初始化echarts实例
      var myChart = echarts.init(this.$refs.graphRef)
      var option

      const axisData = [
        'Mon',
        'Tue',
        'Wed',
        'Very Loooong Thu',
        'Fri',
        'Sat',
        'Sun',
        'Wed',
        'Very Loooong Thu',
        'Fri',
      ]
      const data = axisData.map(function (item, i) {
        console.log(item, i, '111')
        return 10
      })

      // const data = [10, 10, 10, 10, 10, 8, 8, 8, 8, 8]
      const links = data.map(function (item, i) {
        return {
          source: i,
          target: i + 1,
        }
      })
      links.pop()
      option = {
        tooltip: {},
        xAxis: {
          type: 'category',
          show: false,
          boundaryGap: false,
          data: axisData,
        },
        yAxis: {
          show: false,
          type: 'value',
        },
        series: [
          {
            type: 'graph',
            layout: 'none',
            coordinateSystem: 'cartesian2d',
            symbolSize: 40,
            label: {
              show: true,
              position: 'bottom',
            },
            edgeSymbol: ['circle', 'arrow'],
            edgeSymbolSize: [4, 10],
            data: data,
            links: links,
            lineStyle: {
              color: '#red',
            },
          },
        ],
      }

      option && myChart.setOption(option)
    },
  },
}
</script>

<style scoped>
.box {
  width: 1000px;
  height: 500px;
  border: 1px solid #ccc;
  margin: auto;
}
</style>
