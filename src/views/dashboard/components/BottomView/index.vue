<template>
  <div class="bottom-view">
    <div class="view">
      <el-card shadow="hover">
        <template v-slot:header>
          <div class="title-wrapper">关键词搜索</div>
        </template>
        <template>
          <div class="chart-wrapper">
            <div class="chart-inner">
              <div class="chart">
                <div class="chart-title">搜索用户数</div>
                <div class="chart-data">87,263</div>
                <v-chart :options="searchUserOption" :autoresize="true"/>
              </div>
              <div class="chart">
                <div class="chart-title">搜索量</div>
                <div class="chart-data">157,826</div>
                <v-chart :options="searchNumOption" :autoresize="true"/>
              </div>
            </div>
            <div class="table-wrapper">
              <el-table :data="pageTableData">
                <el-table-column prop="rank" label="排名" />
                <el-table-column prop="keyword" label="关键词" />
                <el-table-column prop="count" label="总搜索量" />
                <el-table-column prop="users" label="搜索用户数" />
              </el-table>
              <div class="pagination-wrapper">
                <el-pagination
                  layout="prev, pager, next"
                  :total="14"
                  :page-size="4"
                  background
                  @current-change="onPageChange"
                />
              </div>
            </div>
          </div>
        </template>
      </el-card>
    </div>
    <div class="view">
      <el-card shadow="hover">
        <template v-slot:header>
          <div class="title-wrapper">
            <div class="title">分类销售排行</div>
            <div class="radio-wrapper">
              <el-radio-group v-model="radioSelect" size="small" @change="onCategoryChange">
                <el-radio-button label="品类"></el-radio-button>
                <el-radio-button label="商品"></el-radio-button>
              </el-radio-group>
            </div>
          </div>
        </template>
        <template>
          <div class="chart-wrapper">
            <v-chart :options="categoryOptions" :autoresize="true"/>
          </div>
        </template>
      </el-card>
    </div>
  </div>
</template>

<script>
  const colors = ['#8d7fec', '#5085f2', '#f8726b', '#e7e702', '#78f283', '#4bc1fc']

  export default {
    data() {
      return {
        searchUserOption: {
          xAxis: {
            type: 'category',
            boundaryGap: false,
          },
          yAxis: {
            show: false,
            min: 0,
            max: 210
          },
          series: [{
            type: 'line',
            data: [101,150,200,180,120,80,90],
            areaStyle: {
              color: 'rgba(95,187,255,0.5)'
            },
            lineStyle: {
              color: 'rgba(95,187,255,0.8)'
            },
            itemStyle: {
              opacity: 0
            }
          }],
          grid: {
            top: 0,
            left: 0,
            bottom: 0,
            rigth: 0
          }
        },
        searchNumOption: {
          xAxis: {
            type: 'category',
            boundaryGap: false,
          },
          yAxis: {
            show: false,
            min: 0,
            max: 190
          },
          series: [{
            type: 'line',
            data: [80,120,150,180,150,170,130],
            areaStyle: {
              color: 'rgba(95,187,255,0.5)'
            },
            lineStyle: {
              color: 'rgba(95,187,255,0.8)'
            },
            itemStyle: {
              opacity: 0
            }
          }],
          grid: {
            top: 0,
            left: 0,
            bottom: 0,
            rigth: 0
          }
        },
        tableData: [
          { id:1, rank:1, keyword:'烧烤', count:"24056", users:"1439"},
          { id:2, rank:2, keyword:'快餐', count:"23676", users:"1324"},
          { id:3, rank:3, keyword:'早餐', count:"21256", users:"1314"},
          { id:4, rank:4, keyword:'麦当劳', count:"20043", users:"1221"},
          { id:5, rank:5, keyword:'肯德基', count:"18067", users:"1123"},
          { id:6, rank:6, keyword:'真功夫', count:"17454", users:"1054"},
          { id:7, rank:7, keyword:'东北菜', count:"15236", users:"957"},
          { id:8, rank:8, keyword:'粤菜', count:"12563", users:"912"},
          { id:9, rank:9, keyword:'西餐', count:"10234", users:"818"},
          { id:10, rank:10, keyword:'小炒', count:"9234", users:"713"},
          { id:11, rank:11, keyword:'汤粉', count:"7454", users:"701"},
          { id:12, rank:12, keyword:'奶茶', count:"6534", users:"623"},
          { id:13, rank:13, keyword:'小吃', count:"5344", users:"523"},
          { id:14, rank:14, keyword:'海鲜', count:"3234", users:"498"}
        ],
        PL_Data: [
          {
            legendname: '粉面粥店',
            value: 67,
            percent: '24.87%',
            itemStyle: {
              color: colors[0]
            },
            name: '粉面粥店 | 24.87%'
          },
          {
            legendname: '快餐',
            value: 97,
            percent: '20.00%',
            itemStyle: {
              color: colors[1]
            },
            name: '快餐 | 20.00%'
          },
          {
            legendname: '汉堡披萨',
            value: 86,
            percent: '13.59%',
            itemStyle: {
              color: colors[2]
            },
            name: '汉堡披萨 | 13.59%'
          },
          {
            legendname: '香锅冒菜',
            value: 74,
            percent: '17.69%',
            itemStyle: {
              color: colors[3]
            },
            name: '香锅冒菜 | 17.69%'
          },
          {
            legendname: '小吃炸串',
            value: 73,
            percent: '17.18%',
            itemStyle: {
              color: colors[4]
            },
            name: '小吃炸串 | 17.18%'
          },
          {
            legendname: '地方菜系',
            value: 26,
            percent: '6.67%',
            itemStyle: {
              color: colors[5]
            },
            name: '地方菜系 | 6.67%'
          },
        ],
        SP_Data: [
          {
            legendname: '红烧肉',
            value: 93,
            percent: '23.87%',
            itemStyle: {
              color: colors[0]
            },
            name: '红烧肉 | 23.87%'
          },
          {
            legendname: '烧鸭',
            value: 90,
            percent: '21.30%',
            itemStyle: {
              color: colors[1]
            },
            name: '烧鸭 | 21.30%'
          },
          {
            legendname: '鸡腿堡',
            value: 56,
            percent: '14.59%',
            itemStyle: {
              color: colors[2]
            },
            name: '鸡腿堡 | 14.59%'
          },
          {
            legendname: '馄饨',
            value: 54,
            percent: '16.69%',
            itemStyle: {
              color: colors[3]
            },
            name: '馄饨 | 16.69%'
          },
          {
            legendname: '炸鸡',
            value: 63,
            percent: '18.16%',
            itemStyle: {
              color: colors[4]
            },
            name: '炸鸡 | 18.16%'
          },
          {
            legendname: '肠粉',
            value: 34,
            percent: '8.62%',
            itemStyle: {
              color: colors[5]
            },
            name: '肠粉 | 8.62%'
          }
        ],
        pageTableData: [],
        categoryOptions: {},
        radioSelect: '品类',
        mockData: []
      }
    },
    mounted() {
      this.onPageChange(1)
      this.mockData = this.PL_Data
      this.renderPieChart()
    },
    methods: {
      onCategoryChange(val) {
        console.log(val)
        if (val === "品类") {
          this.mockData = this.PL_Data
          this.renderPieChart()
        } else {
          this.mockData = this.SP_Data
          this.renderPieChart()
        }
      },
      onPageChange(pageIndex) {
        this.pageTableData = this.tableData.slice(4*(pageIndex-1),(pageIndex*4))
      },
      renderPieChart() {
        this.categoryOptions = {
          title: [{
            text: '品类分布',
            textStyle: {
              fontSize: 14,
              color: '#666'
            },
            left: 20,
            top: 20
          }, {
            text: '累计订单量',
            subtext: '320',
            x: '34.5%',
            y: '42.4%',
            textStyle: {
              fontSize: 14,
              color: '#888'
            },
            subtextStyle: {
              fontSize: 28,
              color: '#333'
            },
            textAlign: 'center'
          }],
          series: [{
            type: 'pie',
            data: this.mockData,
            label: {
              normal: {
                show: true,
                position: 'outter',
                formatter: function(params) {
                  return `${params.data.legendname}`
                }
              }
            },
            center: ['35%', '50%'],
            radius: ['40%', '60%'],
            labelLine: {
              normal: {
                length: 14,
                length2: 12,
                smooth: true
              }
            },
            clockwise: true
          }],
          legend: {
            type: 'scroll',
            orient: 'vertical',
            height: 300,
            left: '70%',
            top: 'middle',
            textStyle: {
              color: '#8c8c8c',
              fontSize: 14
            }
          },
          tooltip: {
            trigger: 'item',
            formatter: function (params) {
              const str = params.marker + params.data.legendname + '<br />' +
                '数量：' + params.data.value + '<br />' +
                '占比：' + params.data.percent + '%'
              return str
            }
          }
        }
      }
    }
  }
</script>

<style lang="scss" scoped>
  .bottom-view {
    display: flex;
    margin-top: 20px;

    .view {
      flex: 1;
      width: 50%;
      box-sizing: border-box;

      &:first-child {
        padding: 0 10px 0 0;
      }

      &:last-child {
        padding: 0 0 0 10px;
      }

      .title-wrapper {
        display: flex;
        align-items: center;
        height: 60px;
        box-sizing: border-box;
        border-bottom: 1px solid #eee;
        font-size: 14px;
        font-weight: 500;
        padding: 0 0 0 20px;

        .radio-wrapper {
          flex: 1;
          display: flex;
          justify-content: flex-end;
          padding-right: 20px;
        }
      }

      .chart-wrapper {
        display: flex;
        flex-direction: column;
        height: 452px;

        .chart-inner {
          display: flex;
          padding: 0 10px;
          margin-top: 20px;

          .chart {
            flex: 1;
            padding: 0 10px;

            .chart-title {
              color: #999;
              font-size: 14px;
            }

            .chart-data {
              font-size: 22px;
              color: #333;
              font-weight: 500;
              letter-spacing: 2px;
            }

            .echarts {
              height: 50px;
            }
          }
        }

        .table-wrapper {
          flex: 1;
          margin-top: 20px;
          padding: 0 20px 20px;
          position: relative;

          .pagination-wrapper{
            position: absolute;
            bottom: 15px;
            right: 35px;
            .el-pagination {
              display: flex;
              justify-content: flex-end;
              margin-top: 15px;
            }
          }

          
        }
      }
    }
  }
</style>
