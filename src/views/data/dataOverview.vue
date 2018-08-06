<template>
  <div class="dataOverview">
     <div class="title">
      <div class="title-des"><span >实时概览</span> 
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
      <div class="title-des"><span >商品看板</span> 
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
  name: 'dataOverview',

  data () {
    return {
    }
  },

  methods: {}
}
</script>
<style lang="scss" scoped>
  .dataOverview {
    padding: 15px;
    box-sizing: border-box;
  }
</style>


