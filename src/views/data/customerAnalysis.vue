<template>
  <div class="customerAnalysis">
    <div class="title">
      <div class="title-des"><span >客户概览分析</span> 
    <el-popover
      placement="top-start"
      title="标题"
      width="600"
      trigger="hover"
      content="这是一段内容,这是一段内容,这是一段内容,这是一段内容。">
      <span slot="reference" class="el-icon-info"></span>
    </el-popover>
      </div>
    </div>
    <div class="title">
      <div class="title-des"><span >微信粉丝统计</span> 
    <el-popover
      placement="top-start"
      title="标题"
      width="600"
      trigger="hover"
      content="这是一段内容,这是一段内容,这是一段内容,这是一段内容。">
      <span slot="reference" class="el-icon-info"></span>
    </el-popover>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'customerAnalysis',

  data () {
    return {
    }
  },

  methods: {}
}
</script>
<style lang="scss" scoped>
 .customerAnalysis {
   padding: 15px;
   box-sizing: border-box;
 }
</style>

