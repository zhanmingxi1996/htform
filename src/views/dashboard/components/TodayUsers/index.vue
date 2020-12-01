<template>
  <common-card
    title="今日交易用户数"
    :value="orderUser"
  >
    <template>
      <v-chart :options="getOptions()" :autoresize="true"/>
    </template>
    <template v-slot:footer>
      <span>退货率 </span>
      <span class="emphasis">3.14%</span>
    </template>
  </common-card>
</template>

<script>
  import commonCardMixin from '../../mixins/commonCardMixin'

  export default {
    mixins: [commonCardMixin],
    data() {
      return {
        orderUser: '81086'
      }
    },
    methods: {
      getOptions() {
        return {
          color: ['#3398DB'],
          tooltip: {},
          series: [{
            name: '用户实时交易量',
            type: 'bar',
            data: [410,182,200,334,390,330,220,150,82,200,134,290,330,128],
            barWidth: '60%'
          }],
          xAxis: {
            type: 'category',
            data: this.orderUserTrendAxis,
            show: false
          },
          yAxis: {
            show: false
          },
          grid: {
            top: 0,
            left: 0,
            bottom: 0,
            right: 0
          }
        }
      }
    }
  }
</script>

<style lang="scss" scoped>
</style>
