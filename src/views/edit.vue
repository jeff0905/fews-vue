<template>
  <v-container fluid fill-height pa-0
            v-on:mouseup="mouseUp"
              v-on:mousemove="mouseMove">
    <v-layout row>
      <v-flex xs4 md4 xl4 lg4 sm4>
        <v-tabs color="cyan" dark slider-color="yellow">
          <v-tab>
            选择图标
          </v-tab>
          <v-tab-item>
            <ul class="container-chart" fill-height
              v-on:click="selectChart"
              v-on:mousedown="mouseDown"
              >
              <li class="checked">
                <img src="http://echarts.baidu.com/images/builder/chart/bar.svg" alt=""><input type="checkbox" name="bar">
                <h5>柱状图
                  <div>Bar</div>
                </h5>
              </li>
              <li class="checked"><img src="http://echarts.baidu.com/images/builder/chart/line.svg" alt=""><input type="checkbox" name="line">
                <h5>折线图
                  <div>Line</div>
                </h5>
              </li>
              <li class="checked"><img src="http://echarts.baidu.com/images/builder/chart/pie.svg" alt=""><input type="checkbox" name="pie">
                <h5>饼图
                  <div>Pie</div>
                </h5>
              </li>
              <li><img src="http://echarts.baidu.com/images/builder/chart/scatter.svg" alt=""><input type="checkbox" name="scatter">
                <h5>散点图
                  <div>Scatter</div>
                </h5>
              </li>
              <li><img src="http://echarts.baidu.com/images/builder/chart/candlestick.svg" alt=""><input type="checkbox" name="candlestick">
                <h5>K线图
                  <div>Candlestick</div>
                </h5>
              </li>
              <li><img src="http://echarts.baidu.com/images/builder/chart/radar.svg" alt=""><input type="checkbox" name="radar">
                <h5>雷达图
                  <div>Radar</div>
                </h5>
              </li>
              <li><img src="http://echarts.baidu.com/images/builder/chart/heatmap.svg" alt=""><input type="checkbox" name="heatmap">
                <h5>热力图
                  <div>Heatmap</div>
                </h5>
              </li>
              <li><img src="http://echarts.baidu.com/images/builder/chart/tree.svg" alt=""><input type="checkbox" name="tree">
                <h5>树图
                  <div>Tree</div>
                </h5>
              </li>
              <li><img src="http://echarts.baidu.com/images/builder/chart/treemap.svg" alt=""><input type="checkbox" name="treemap">
                <h5>矩形树图
                  <div>Treemap</div>
                </h5>
              </li>
              <li><img src="http://echarts.baidu.com/images/builder/chart/sunburst.svg" alt=""><input type="checkbox" name="sunburst">
                <h5>旭日图
                  <div>Sunburst</div>
                </h5>
              </li>
              <li><img src="http://echarts.baidu.com/images/builder/chart/map.svg" alt=""><input type="checkbox" name="map">
                <h5>地图
                  <div>Map</div>
                </h5>
              </li>
              <li><img src="http://echarts.baidu.com/images/builder/chart/lines.svg" alt=""><input type="checkbox" name="lines">
                <h5>线图
                  <div>Lines</div>
                </h5>
              </li>
              <li><img src="http://echarts.baidu.com/images/builder/chart/graph.svg" alt=""><input type="checkbox" name="graph">
                <h5>关系图
                  <div>Graph</div>
                </h5>
              </li>
              <li><img src="http://echarts.baidu.com/images/builder/chart/boxplot.svg" alt=""><input type="checkbox" name="boxplot">
                <h5>箱线图
                  <div>Boxplot</div>
                </h5>
              </li>
              <li><img src="http://echarts.baidu.com/images/builder/chart/parallel.svg" alt=""><input type="checkbox" name="parallel">
                <h5>平行坐标
                  <div>Parallel</div>
                </h5>
              </li>
              <li><img src="http://echarts.baidu.com/images/builder/chart/gauge.svg" alt=""><input type="checkbox" name="gauge">
                <h5>仪表盘
                  <div>Gauge</div>
                </h5>
              </li>
              <li><img src="http://echarts.baidu.com/images/builder/chart/funnel.svg" alt=""><input type="checkbox" name="funnel">
                <h5>漏斗图
                  <div>Funnel</div>
                </h5>
              </li>
              <li><img src="http://echarts.baidu.com/images/builder/chart/sankey.svg" alt=""><input type="checkbox" name="sankey">
                <h5>桑基图
                  <div>Sankey</div>
                </h5>
              </li>
              <li><img src="http://echarts.baidu.com/images/builder/chart/themeRiver.svg" alt=""><input type="checkbox" name="themeRiver">
                <h5>主题河流图
                  <div>ThemeRiver</div>
                </h5>
              </li>
              <li><img src="http://echarts.baidu.com/images/builder/chart/pictorialBar.svg" alt=""><input type="checkbox" name="pictorialBar">
                <h5>象形柱图
                  <div>PictorialBar</div>
                </h5>
              </li>
              <li><img src="http://echarts.baidu.com/images/builder/chart/custom.svg" alt=""><input type="checkbox" name="custom">
                <h5>自定义系列
                  <div>Custom</div>
                </h5>
              </li>
            </ul>
          </v-tab-item>
        </v-tabs>
      </v-flex>
      <v-flex>
        <v-container column class="dragContainer" fill-height ref="dragContainer">

          <canvas id="grid" ref="grid" />
          <div v-for="item in list" :key="item.id" class="item">
              {{item.name}}
          </div>
        </v-container>
      </v-flex>


              <li id='temp' style='width:200px;height:200px;display:none'>
                <img src="http://echarts.baidu.com/images/builder/chart/custom.svg" width="200px" height="100px" alt=""><input type="checkbox" name="custom">
                <h5>自定义系列
                  <div>Custom</div>
                </h5>
              </li>
    </v-layout>
  </v-container>
</template>

<script>
/**
 * TODOS: 1. canvas grid 的容器宽高问题.

 */

// drag..
// import $ from 'jquery'
// import 'jquery-ui'
// import 'jquery-ui/themes/base/core.css'
// import 'jquery-ui/themes/base/theme.css'
// import 'jquery-ui/themes/base/draggable.css'
// import 'jquery-ui/ui/core'
// import 'jquery-ui/ui/widgets/draggable'

export default {
  name: 'Edit',
  data: () => (
    {
      list: [],
      draggable: {
        canDrag: false
      }
    }
  ),
  mounted: function () {
    this.getContainerRect()
    this.drawGrid(this.$refs.grid, '#ddd', 4, 4)
    this.initDrag()
  },
  methods: {
    // 初始化drag
    initDrag () {
      // console.log($('.container-chart li'))
      // $('.container-chart li').each((index, item) => {
      //   console.log($(item))
      //   $(item).draggable({
      //     containment: 'document.body'
      //   })
      // })
    },
    mouseDown ($event) {
      console.log('mouse down', $event, this.getCoor($event))
      const coor = this.getCoor($event)
      const position = `display:block;position:absolute;top:${coor.y}px;left:${coor.x}px`
      document.getElementById('temp').setAttribute('style', position)
      this.draggable.canDrag = true
    },
    mouseMove ($event) {
      if (this.draggable.canDrag) {

      console.log('mouse move')
      const coor = this.getCoor($event)
      const position = `display:block;position:absolute;top:${coor.y}px;left:${coor.x}px`
      document.getElementById('temp').setAttribute('style', position)
      }
    },
    mouseUp () {
      console.log('mouse up')
      if (this.draggable.canDrag) {

      console.log('mouse move')
      const coor = this.getCoor($event)
      const position = `display:block;position:absolute;top:${coor.y}px;left:${coor.x}px`
      document.getElementById('temp').setAttribute('style', position)
      }
      this.draggable.canDrag = false
    },

    getCoor ($event) {
      const {x, y} = $event
      return {x, y}
    },

    selectChart (type = 'line') {
      this.list.push({id: Math.random(), name: 'line', type: 'line'})
    },

    getContainerRect (selector) {
      const rect = this.$refs.dragContainer.getBoundingClientRect()
      console.log({rect})
      return rect
    },
    // 模糊, 边界问题.
    drawGrid (container, color, stepx, stepy) {
      // const rect = this.$refs.grid.getBoundingClientRect()
      const containerRect = this.getContainerRect()
      const context = container.getContext('2d')
      const width = context.canvas.width = parseInt(containerRect.width)
      const height = context.canvas.height = parseInt(containerRect.height)
      context.strokeStyle = color
      context.lineWidth = 0.5
      context.clearRect(0, 0, width, height)
      console.log(width, height)
      for (let i = stepx + 0.5; i < width; i += stepx) {
        context.beginPath()
        context.moveTo(i, 0)
        context.lineTo(i, height)
        context.stroke()
      }
      for (let j = stepy + 0.5; j < height; j += stepy) {
        context.beginPath()
        context.moveTo(0, j)
        context.lineTo(width, j)
        context.stroke()
      }
      context.restore()
    }
  }
}
</script>

<style lang="less">

@import "./edit.less";
</style>
