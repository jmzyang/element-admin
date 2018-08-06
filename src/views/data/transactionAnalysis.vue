<template>
  <div class="transactionAnalysis">
      <div class="title">
      <div class="title-des"><span >商品概览</span> 
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
      <div class="title-des"><span >商品效果</span> 
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
  name: 'transactionAnalysis',

  data () {
    return {
    }
  },

  methods: {}
}
</script>
<style lang="scss" scoped>
  .transactionAnalysis {
    padding: 15px;
    box-sizing: border-box;
  }
</style>


