<template>
  <common-card
    title="累计销售额"
    :value="salesToday"
  >
    <template>
      <div class="compare-wrapper">
        <div class="compare">
          <span>日同比</span>
          <span class="emphasis">7.28%</span>
          <div class="increase" />
        </div>
        <div class="compare">
          <span>月同比</span>
          <span class="emphasis">36.88%</span>
          <div class="decrease" />
        </div>
      </div>
    </template>
    <template v-slot:footer>
      <span>昨日销售额 </span>
      <span class="emphasis">￥3,204,919</span>
    </template>
  </common-card>
</template>

<script>
  import commonCardMixin from '../../mixins/commonCardMixin'

  export default {
    mixins: [commonCardMixin],
    data() {
      return {
        salesToday: '￥32,766,686'
      }
    }
  }
</script>

<style lang="scss" scoped>
  .compare-wrapper {
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;

    .compare {
      display: flex;
      align-items: center;
      font-size: 12px;
      margin-top: 3px;
      color: #666;
    }
  }
</style>
