<template>
  <div class="body">
    <div class="title">
      <div>Dashboard</div>
      <div>
        <span>10-06-2021 <img src="@/assets/Vector.png" alt="" /></span>
        <span>10-10-2021 <img src="@/assets/Vector.png" alt="" /></span>
      </div>
    </div>
    <div class="indicator">
      <div class="idr">
        <div><img src="@/assets/Icon.png" alt="" /></div>
        <div>
          <div>178+</div>
          <div>Save Products</div>
        </div>
      </div>
      <div class="idr">
        <div><img src="@/assets/Icon (1).png" alt="" /></div>
        <div>
          <div>20+</div>
          <div>Stock Products</div>
        </div>
      </div>
      <div class="idr">
        <div><img src="@/assets/Incon.png" alt="" /></div>
        <div>
          <div>190+</div>
          <div>Sales Products</div>
        </div>
      </div>
      <div class="idr">
        <div><img src="@/assets/Icon (2).png" alt="" /></div>
        <div>
          <div>12+</div>
          <div>Job Application</div>
        </div>
      </div>
    </div>
    <div class="charts">
      <div class="line" id="line"></div>
      <div class="pie" id="pie"></div>
    </div>
    <div class="detail">
      <div class="table">
        <el-table :data="tableData" style="width: 100%">
          <el-table-column prop="date" label="日期" width="180">
          </el-table-column>
          <el-table-column prop="name" label="姓名" width="180">
          </el-table-column>
          <el-table-column prop="address" label="地址"> </el-table-column>
        </el-table>
      </div>
      <div class="top">
        <div class="top-title">Top Selling Products</div>
        <div class="product">
            <img src="@/assets/Mask Group.png" alt="">
            <div>
                <div>NIKE Shoes Black Pattern</div>
                <img src="@/assets/Group 525.png" alt="">
                <div class="dollar">$87</div>
            </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import * as echarts from "echarts";
export default {
  name: "myBody",
  data() {
    return {
      tableData: [
        {
          date: "2016-05-02",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1518 弄",
        },
        {
          date: "2016-05-04",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1517 弄",
        },
        {
          date: "2016-05-01",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1519 弄",
        },
        {
          date: "2016-05-03",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1516 弄",
        },
      ],
    };
  },
  mounted() {
    this.initLine();
    this.initPie();
  },
  methods: {
    initLine() {
      var chartDom = document.getElementById("line");
      var myChart = echarts.init(chartDom);
      var option;

      option = {
        title: {
          show: true,
          text: "Reports",
        },
        xAxis: {
          type: "category",
          data: ["Mon", "Tue", "Wed", "Thu", "Fri", "Sat", "Sun"],
        },
        yAxis: {
          type: "value",
          show: true,
          axisTick: {
            //y轴刻度线
            show: true,
          },
          axisLine: {
            //y轴
            show: true,
          },
        },
        series: [
          {
            data: [820, 932, 901, 934, 1290, 1330, 1320],
            type: "line",
            smooth: true,
          },
        ],
      };

      option && myChart.setOption(option);
    },
    initPie() {
      var chartDom = document.getElementById("pie");
      var myChart = echarts.init(chartDom);
      var option;

      option = {
        title: {
          show: true,
          text: "Analytics",
        },
        tooltip: {
          trigger: "item",
        },
        legend: {
          top: "5%",
          left: "center",
        },
        series: [
          {
            name: "Access From",
            type: "pie",
            radius: ["40%", "70%"],
            avoidLabelOverlap: false,
            itemStyle: {
              borderRadius: 10,
              borderColor: "#fff",
              borderWidth: 2,
            },
            label: {
              show: false,
              position: "center",
            },
            emphasis: {
              label: {
                show: true,
                fontSize: "40",
                fontWeight: "bold",
              },
            },
            labelLine: {
              show: false,
            },
            data: [
              { value: 1048, name: "Search Engine" },
              { value: 735, name: "Direct" },
              { value: 580, name: "Email" },
              { value: 484, name: "Union Ads" },
              { value: 300, name: "Video Ads" },
            ],
          },
        ],
      };

      option && myChart.setOption(option);
    },
  },
};
</script>
<style lang="scss" scoped>
.body {
  .title {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-top: 35px;
    padding: 0 30px;
    > div:nth-child(1) {
      color: rgb(3, 2, 41);
      font-family: Nunito;
      font-size: 24px;
      font-weight: 700;
      line-height: 33px;
    }
    > div:nth-child(2) {
      display: flex;
      span {
        color: rgb(3, 2, 41);
        font-family: Nunito;
        font-size: 14px;
        font-weight: 600;
        line-height: 19px;
        margin-right: 15px;
        padding: 10px 17px;
        img {
          vertical-align: middle;
        }
      }
    }
  }
  .indicator {
    margin: 0 30px;
    display: flex;
    align-items: center;
    .idr {
      display: flex;
      width: 268px;
      height: 116px;
      padding: 28px;
      align-items: center;
      margin-right: 30px;
      > div:nth-child(1) {
        img {
          width: 60px;
          height: 60px;
        }
      }
      > div:nth-child(2) {
        margin-left: 23px;
        > div:nth-child(1) {
          color: rgb(0, 0, 0);
          font-family: Nunito;
          font-size: 22px;
          font-weight: 800;
          line-height: 30px;
        }
        > div:nth-child(2) {
          color: rgb(3, 2, 41);
          font-family: Nunito;
          font-size: 14px;
          font-weight: 400;
          line-height: 19px;
        }
      }
    }
  }
  .charts {
    display: flex;
    padding: 0 30px;
    height: 408px;
    .line {
      width: 60%;
    }
    .pie {
      width: 30%;
    }
  }
  .detail {
    padding: 0 30px;
    display: flex;
    .table {
      width: 70%;
    }
    .top {
      width: 25%;
      padding: 25px 0 25px 25px;
        .top-title {
            color: rgb(0, 0, 0);
            font-family: Nunito;
            font-size: 18px;
            font-weight: 700;
            line-height: 25px;
        }
        .product {
            margin-top: 25px;
            display: flex;
            > div {
                > div:nth-child(1) {
                    margin: 10px 25px;
                }
                img {
                    margin-left: 25px;
                }
                .dollar {
                    margin-left: 25px;
                    margin-top: 10px;
                }
            }
        }
    }
  }
}
</style>