<template>
  <div class="top-view-container">
    <el-row :gutter="8">
      <el-col :span="6">
        <el-card shadow="hover">
          <total-sales />
        </el-card>
      </el-col>
      <el-col :span="6">
        <el-card shadow="hover">
          <total-orders />
        </el-card>
      </el-col>
      <el-col :span="6">
        <el-card shadow="hover">
          <today-users />
        </el-card>
      </el-col>
      <el-col :span="6">
        <el-card shadow="hover">
          <total-users />
        </el-card>
      </el-col>
    </el-row>
  </div>
</template>

<script>
  import TotalSales from '../TotalSales'
  import TotalOrders from '../TotalOrders'
  import TodayUsers from '../TodayUsers'
  import TotalUsers from '../TotalUsers'

  export default {
    components: {
      TotalSales,
      TotalOrders,
      TodayUsers,
      TotalUsers
    }
  }
</script>

<style lang="scss" scoped>
  .top-view-container {
    padding: 15px 0px 0px 0px;
  }
</style>