<template>
  <div class="dataAna">
    <div class="title">
      <div class="title-des"><span >交易概览</span> 
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
  name: 'dataAna',

  data () {
    return {
    }
  },

  methods: {}
}
</script>
<style lang="scss" scoped>
 .dataAna {
   padding: 15px;
   box-sizing: border-box;
 }
</style>
