<template>
  <!-- <div style="height: 100px; overflow: scroll"> -->
  <div class="box" ref="graphRef"></div>
  <!-- </div> -->
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
      const cols = 8 // 定义多少列
      const links = []
      const edges = []
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
      axisData.forEach((item, i) => {
        const row = Math.ceil((i + 1) / cols) // 计算8列，共计多少行
        const col = cols - Math.abs((i % (2 * cols)) - cols) + (row % 2) // 计算当前行，一共多少列，且给出每列的位置

        // links主要用于确定连线谁连着谁
        links.push({
          source: i,
          target: i + 1,
          value: '',
          label: {
            show: true,
            formatter: '{c}',
          },
        })

        // edges主要用于确定连线位置,以便于节点之间换行
        edges.push({
          name: i,
          x: col * 100,
          y: row * 100,
        })
      })
      option = {
        series: [
          {
            type: 'graph',
            symbolSize: 50,
            data: edges,
            links,
            label: {
              show: true,
              position: 'bottom',
            },
            edgeSymbol: ['none', 'arrow'],
            lineStyle: {
              width: 1,
              show: true,
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
  height: 800px;
  border: 1px solid #ccc;
  margin: auto;
}
</style>
