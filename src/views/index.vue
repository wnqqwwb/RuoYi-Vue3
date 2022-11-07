<template>
  <div id="home">
    <el-row :gutter="20">
      <el-col :span="16">
        <el-card class="box-card" shadow="hover">
          <div slot="header" class="clearfix">
            <span>客房入住率</span>
          </div>
          <div id="liveRate" style="left:0;width: 100%;height: 250px"></div>
        </el-card>
      </el-col>
      <el-col :span="8">
        <el-card class="box-card" shadow="hover">
          <div slot="header" class="clearfix">
            <span>房型比例</span>
          </div>
          <div id="roomType" style="left:0;width: 100%;height: 250px"></div>
        </el-card>
      </el-col>
    </el-row>
    <el-row :gutter="20">
      <el-col :span="16">
        <el-card class="box-card" shadow="hover">
          <div slot="header" class="clearfix">
            <span>预定量</span>
          </div>
          <div id="order" style="left:0;width: 100%;height: 250px"></div>
        </el-card>
      </el-col>
      <el-col :span="8">
        <el-card class="box-card" shadow="hover">
          <div slot="header" class="clearfix">
            <span>客房入住比例</span>
          </div>
          <div id="orderType" style="left:0;width: 100%;height: 250px"></div>
        </el-card>
      </el-col>
    </el-row>
  </div>
</template>

<script>
import * as echarts from 'echarts';



export default {
  name: 'Home',
  data(){
    return{
      roomNumber: null,
      dialogFormVisible: false,
      userCount: 1203,
      orderCount: 12032,
      form: {
        name: '',
        phone: ''
      },
      isOrderShown: false,
      order: null,
    }
  },

  mounted() {
    this.rtChart()
    this.lrChart()
    this.orderChart()
    this.ortChart()
  },
  methods:{

    rtChart(){
      var rtChart = echarts.init(document.getElementById('roomType'), 'light');
      rtChart.setOption({
        tooltip: {},
        series: [{
          name: '比例',
          type: 'pie',
          radius: '55%',
          data: [
            {value: 35, name: '单人房'},
            {value: 55, name: '大床房'},
            {value: 45, name: '双床房'},
            {value: 55, name: '商务大床房'},
            {value: 45, name: '商务双床房'},
            {value: 35, name: '豪华大床房'},
          ]
        }]
      });
    },
    lrChart(){
      var myChart =  echarts.init(document.getElementById('liveRate'),'light')
      myChart.setOption({

        xAxis: {
          type: 'category',
          data: [1,2,3,4,5,6,7,8,9,10,11,12],
          axisLabel: {
            formatter: '{value} 月'
          }
        },
        yAxis: {
          type: 'value',
          axisLabel: {
            formatter: '{value} %'
          }
        },
        series: [{
          data: [50, 68, 55.4, 53.2, 76.6, 80.6, 47.6,45.7,67.2,58.3,78.4,94.2],
          type: 'line'
        }]
      });
    },
    orderChart(){
      var myChart =  echarts.init(document.getElementById('order'),'light')
      myChart.setOption({
        itemStyle:{
          color: '#409EFF',
        },
        tooltip : {
          trigger: 'axis',
          axisPointer : {            // 坐标轴指示器，坐标轴触发有效
            type : 'line'        // 默认为直线，可选为：'line' | 'shadow'
          },
        },
        xAxis: {
          type: 'category',
          data: [1,2,3,4,5,6,7,8,9,10,11,12],
          axisLabel: {
            formatter: '{value} 月'
          }
        },
        yAxis: {
          type: 'value',
          axisLabel: {
            formatter: '{value} 单'
          }
        },
        series: [{
          name: '订单量',
          data: [432, 568, 469, 532, 766, 806, 476,457,672,583,784,942],
          type: 'bar'
        }]
      });
    },
    ortChart(){
      var rtChart =  echarts.init(document.getElementById('orderType'),'light')
      rtChart.setOption({
        tooltip: {},
        series: [{
          name: '比例',
          type: 'pie',
          radius: '55%',
          data: [
            {value: 35, name: '单人房'},
            {value: 15, name: '大床房'},
            {value: 10, name: '双床房'},
            {value: 15, name: '商务大床房'},
            {value: 5, name: '商务双床房'},
            {value: 20, name: '豪华大床房'},
          ]
        }]
      });
    },
  },
}
</script>

<style scoped>

.el-row {
  margin: 10px 5px;
}
.el-card{
  text-align: center;
}
</style>
