<template>
  <div class="container">
    <div class="header">
      销售数据报表展示
    </div>
    <top-view />
    <sales-view />
    <bottom-view />
    <map-view />
  </div>
</template>

<script>
  import topView from './components/TopView/index'
  import salesView from './components/SalesView/index'
  import bottomView from './components/BottomView/index'
  import mapView from './components/MapView/index'

  export default {
    name: 'Dashboard',
    components: {
      topView,
      salesView,
      bottomView,
      mapView 
    }
  };
</script>

<style lang="scss" scoped>
  .container {
    width: 100%;
    height: 100%;
    padding: 10px;
    background: #eee;
    .header {
      font-size: 30px;
      color: #444;
      padding: 10px;
      background: #fff;
      text-align: center;
      border-radius: 6px;
    }
  }
</style>
