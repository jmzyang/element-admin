<template>
  <div class="merchandiseControl">
      <div class="operate">
        <div>
          <el-select v-model="value" placeholder="请选择" class="sel state">
            <el-option
              v-for="item in options"
              :key="item.value"
              :label="item.label"
              :value="item.value">
            </el-option>
          </el-select>
           <el-select v-model="value" placeholder="请选择" class="sel group">
            <el-option
              v-for="item in options"
              :key="item.value"
              :label="item.label"
              :value="item.value">
            </el-option>
          </el-select>
           <el-select v-model="value" placeholder="请选择" class="sel label">
            <el-option
              v-for="item in options"
              :key="item.value"
              :label="item.label"
              :value="item.value">
            </el-option>
          </el-select>
             <div class="search">
              <el-select v-model="value" placeholder="请选择">
                <el-option
                  v-for="item in options"
                  :key="item.value"
                  :label="item.label"
                  :value="item.value">
                </el-option>
              </el-select>
              <el-input
              size="mini"
              placeholder="请输入内容"
              suffix-icon="el-icon-search"
              v-model="input9"
              id="search-input">
              </el-input>
            </div>
        </div>
        <div style="margin-top:10px">
          <el-tag @click.native="addMerchandise">新增商品</el-tag>
        </div>
      </div>
      <el-table
      ref="multipleTable"
      :data="tableData3"
      tooltip-effect="dark"
      style="width: 100%"
      @selection-change="handleSelectionChange">
      <el-table-column
        type="selection"
        width="55">
      </el-table-column>
      <el-table-column
        label="日期"
        width="120">
        <template slot-scope="scope">{{ scope.row.date }}</template>
      </el-table-column>
      <el-table-column
        prop="money"
        label="价格"
        width="120">
      </el-table-column>
      <el-table-column
        prop="name"
        label="姓名"
        width="120">
      </el-table-column>
      <el-table-column
        prop="status"
        label="状态"
        show-overflow-tooltip>
      </el-table-column>
      <el-table-column
        prop="inventory"
        label="库存"
        show-overflow-tooltip>
      </el-table-column>
      <el-table-column
        prop="sales"
        label="销量"
        show-overflow-tooltip>
      </el-table-column>
      <el-table-column
        prop="id"
        label="序号"
        sortable
        show-overflow-tooltip>
      </el-table-column>
    
    </el-table>
    <div style="margin-top: 20px">
    <el-pagination
      @size-change="handleSizeChange"
      @current-change="handleCurrentChange"
      :current-page="currentPage1"
      :page-sizes="[8, 9, 10, 20]"
      :page-size="100"
      layout="total, sizes, prev, pager, next, jumper"
      :total="100">
    </el-pagination>
    </div>
    <el-dialog title="收货地址" :visible.sync="dialogTableVisible">
    <div v-for="(item,key) in multipleSelection" :key="key">
      {{item.name}} - <el-select v-model="value" placeholder="请选择" class="sel state">
            <el-option
              v-for="item in options"
              :key="item.value"
              :label="item.label"
              :value="item.value">
            </el-option>
          </el-select>
    </div>
    <div slot="footer" class="dialog-footer">
    <el-button @click="dialogTableVisible = false">取 消</el-button>
    <el-button type="primary" @click="dialogTableVisible = false">确 定</el-button>
  </div>
</el-dialog>
  </div>
</template>

<script>
export default {
  name: 'merchandiseControl',

  data () {
    return {
      title:'商品管理界面',
      tableData3: [{
          date: '2016-05-03',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄',
          money:88,
          inventory:100,
          sales:88,
          status:'上架',
          id:'1'
        }, {
          date: '2016-05-02',
          name: '王小虎2',
          address: '上海市普陀区金沙江路 1518 弄',
          money:90,
          inventory:100,
          sales:88,
          status:'上架',
          id:'2'
        }, {
          date: '2016-05-04',
          name: '王小虎3',
          address: '上海市普陀区金沙江路 1518 弄',
          money:92,
          inventory:100,
          sales:88,
          status:'上架',
          id:'3'
        }, {
          date: '2016-05-01',
          name: '王小虎4',
          address: '上海市普陀区金沙江路 1518 弄',
          money:94,
          inventory:100,
          sales:88,
          status:'下架',
          id:'4'
        }, {
          date: '2016-05-08',
          name: '王小虎5',
          address: '上海市普陀区金沙江路 1518 弄',
          money:96,
          inventory:100,
          sales:88,
          status:'上架',
          id:'5'
        }, {
          date: '2016-05-06',
          name: '王小虎6',
          address: '上海市普陀区金沙江路 1518 弄',
          money:98,
          inventory:100,
          sales:88,
          status:'下架',
          id:'6'
        }, {
          date: '2016-05-07',
          name: '王小虎7',
          address: '上海市普陀区金沙江路 1518 弄',
          money:100,
          inventory:100,
          sales:88,
          status:'上架',
          id:'7'
        }, {
          date: '2016-05-07',
          name: '王小虎7',
          address: '上海市普陀区金沙江路 1518 弄',
          money:100,
          inventory:100,
          sales:88,
          status:'上架',
          id:'8'
        }, {
          date: '2016-05-07',
          name: '王小虎7',
          address: '上海市普陀区金沙江路 1518 弄',
          money:100,
          inventory:100,
          sales:88,
          status:'上架',
          id:'9'
        }],
        multipleSelection: [],
         currentPage1: 1,
        currentPage2: 5,
        currentPage3: 5,
        currentPage4: 4,
         options: [{
          value: '选项1',
          label: '黄金糕'
        }, {
          value: '选项2',
          label: '双皮奶'
        }, {
          value: '选项3',
          label: '蚵仔煎'
        }, {
          value: '选项4',
          label: '龙须面'
        }, {
          value: '选项5',
          label: '北京烤鸭'
        }],
        value: '',
        input9:'',
        dialogTableVisible: false,
    }
  },

  methods: {
    toggleSelection(rows) {
      if (rows) {
        rows.forEach(row => {
          this.$refs.multipleTable.toggleRowSelection(row);
        });
      } else {
        this.$refs.multipleTable.clearSelection();
      }
    },
    handleSelectionChange(val) {
      this.multipleSelection = val;
    },
    handleSizeChange(val) {
      console.log(`每页 ${val} 条`);
    },
    handleCurrentChange(val) {
      console.log(`当前页: ${val}`);
    },
    test(){
      console.log('aaa');
    },
    addMerchandise(){
      this.$router.push('/merchandise/merchandise-add');
    },
    upMerchandise(){
      this.multipleSelection.forEach(item=>{
        if (item.status=='下架') {
          item.status = '上架';
        }
      })
    },
    downMerchandise(){
      this.multipleSelection.forEach(item=>{
        if (item.status=='上架') {
          item.status = '下架';
        }
      })
    },
    delMerchandise(){
       this.tableData3 = this.tableData3.filter(item=>{
         return !this.multipleSelection.includes(item);
       })
    },
    handleDelete(i,row){
      this.tableData3.splice(i,1);
    },
    handleEdit(i,row){
      this.$router.push({
        name:'editMerchandise',
        query:{
          index:i
        }
      });
    },
    editMerchandiseGroup(){
      if (!this.multipleSelection.length) {
         this.$notify({
          title: '错误的操作',
          message: '您还未选中商品...'
        });
      }else {
         this.dialogTableVisible = true
      }
    }
  }
}
</script>

<style scoped>
  .merchandiseControl {
    padding: 15px;
  }
  .operate {
    height: 100px;
    box-sizing: border-box;
    padding: 10px;
    background: rgba(252,252,252,.9);
    position: relative;
  }
  .sel {
    margin-right: 30px;
  }
 
  
</style>
