<template>
  <div class="allOrder">
    <div class="allOrderControll">
      <div>
              <el-select v-model="value" placeholder="请选择">
        <el-option
          v-for="item in options"
          :key="item.value"
          :label="item.label"
          :value="item.value">
        </el-option>
      </el-select>
    <el-date-picker
      v-model="value7"
      type="daterange"
      align="right"
      unlink-panels
      range-separator="至"
      start-placeholder="开始日期"
      end-placeholder="结束日期"
      :picker-options="pickerOptions2">
    </el-date-picker>
   
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
          <el-tag>全部</el-tag>
          <el-tag type="success">待付款</el-tag>
          <el-tag type="info">待发货</el-tag>
          <el-tag type="warning">已发货</el-tag>
          <el-tag type="danger">已完成</el-tag>
          <el-tag>已关闭</el-tag>
          <el-tag type="success">退款中</el-tag>
        </div>
 
    </div>
    <table class="protitle">
      <tr class="theadsty">
          <th>商品信息</th>
          <th>单价</th>
          <th>数量</th>
          <th>售后</th>
          <th>买家</th>
          <th>下单时间</th>
          <th>订单状态</th>
          <th>实付金款</th>
        </tr>
    </table>
      <div v-for="(item,i) in orders" :key="i">
    <table>
      <tbody>     
        <tr class="theadsty">
        </tr>
        <tr>
          <td colspan="8" class="orderId">
            订单编号:{{item.orderid}}
            <div class="active orderdetail">查看详情</div>
          </td>
        </tr>
        <tr class="itemsty">
          <td>
            <div v-for="(good,i) in item.goods" :key="i">
             <div class="good-item"> <img :src="good.img" alt="">{{good.name}}</div>
            </div>
          </td>
          <td>
            <div v-for="(good,i) in item.goods" :key="i">
             <div class="good-item">¥{{good.danjia}}</div>
            </div>
          </td>
          <td>
            <div v-for="(good,i) in item.goods" :key="i">
             <div class="good-item">{{good.shuliang}}</div>
            </div>
          </td>
          <td>{{item.shouhou}}</td>
          <td class="active">{{item.maijia}}</td>
          <td>{{item.date}}</td>
          <td><div>{{item.state}}</div><div class="active cancelOrder">取消订单</div></td>
          <td>{{item.money}}</td>
        </tr>
      </tbody>   
    </table>  
  </div>
  <div class="block" >
    <el-pagination
      @size-change="handleSizeChange"
      @current-change="handleCurrentChange"
      :current-page.sync="currentPage1"
      :page-size="100"
      layout="total, prev, pager, next"
      :total="1000">
    </el-pagination>
  </div>
  </div>
</template>

<script>
export default {
  name: "allOrder",

  data() {
    return {
      options: [
        {
          value: "选项1",
          label: "黄金糕"
        },
        {
          value: "选项2",
          label: "双皮奶"
        },
        {
          value: "选项3",
          label: "蚵仔煎"
        },
        {
          value: "选项4",
          label: "龙须面"
        },
        {
          value: "选项5",
          label: "北京烤鸭"
        }
      ],
      value: "",
      input9:'',
      orders:[
        {
          goods:[
            {
              img:'https://www.easyicon.net/api/resizeApi.php?id=26823&size=128',
              name:'博士',
              danjia:58,
              shuliang:1
            },
            {
              img:'https://www.easyicon.net/api/resizeApi.php?id=3824&size=128',
              name:'安卓',
              danjia:68,
              shuliang:1
            },
            {
              img:'https://www.easyicon.net/api/resizeApi.php?id=2221&size=128',
              name:'老师',
              danjia:78,
              shuliang:1
            }
          ],
          shouhou:'拒绝',
          maijia:'胡晶',
          date:'2017-8-12 12:12:22',
          state:'未付款',
          money:'58',
          orderid:'ASDXVKXJVISHF1725414'
        },
         {
          goods:[
            {
              img:'https://www.easyicon.net/api/resizeApi.php?id=26823&size=128',
              name:'博士',
              danjia:58,
              shuliang:1
            },
            {
              img:'https://www.easyicon.net/api/resizeApi.php?id=3824&size=128',
              name:'安卓',
              danjia:68,
              shuliang:1
            },
            {
              img:'https://www.easyicon.net/api/resizeApi.php?id=2221&size=128',
              name:'老师',
              danjia:78,
              shuliang:1
            }
          ],
          shouhou:'拒绝',
          maijia:'胡晶',
          date:'2017-8-12 12:12:22',
          state:'未付款',
          money:'58',
          orderid:'ASDXVKXJVISHF1725414'
        }
      ],
      pickerOptions2: {
        shortcuts: [
          {
            text: "最近一周",
            onClick(picker) {
              const end = new Date();
              const start = new Date();
              start.setTime(start.getTime() - 3600 * 1000 * 24 * 7);
              picker.$emit("pick", [start, end]);
            }
          },
          {
            text: "最近一个月",
            onClick(picker) {
              const end = new Date();
              const start = new Date();
              start.setTime(start.getTime() - 3600 * 1000 * 24 * 30);
              picker.$emit("pick", [start, end]);
            }
          },
          {
            text: "最近三个月",
            onClick(picker) {
              const end = new Date();
              const start = new Date();
              start.setTime(start.getTime() - 3600 * 1000 * 24 * 90);
              picker.$emit("pick", [start, end]);
            }
          }
        ]
      },
      value6: "",
      value7: "",
      currentPage1: 5,
        currentPage2: 5,
        currentPage3: 5,
        currentPage4: 4
    };
  },

  methods: {
     handleEdit(index, row) {
        console.log(index, row);
      },
      handleDelete(index, row) {
        console.log(index, row);
      },
      handleSizeChange(val) {
        console.log(`每页 ${val} 条`);
      },
      handleCurrentChange(val) {
        console.log(`当前页: ${val}`);
      }
  }
};
</script>
<style scoped>
.allOrder {
  padding: 15px;
  font-size: 14px;
}
.allOrderControll {
  height: 100px;
  box-sizing: border-box;
  padding: 10px;
  background: rgba(252, 252, 252, 0.9);
  position: relative;
}

 .demo-table-expand {
    font-size: 0;
  }
table {
  width: 100%;
}
  .demo-table-expand label {
    width: 90px;
    color: #99a9bf;
  }
  .demo-table-expand .el-form-item {
    margin-right: 0;
    margin-bottom: 0;
    width: 50%;
  }
  tr {
    min-width: 120px;
  }
  td {
    text-align: center;
    border-bottom: 1px solid #efefef;
    padding: 5px 0;
  }
 tbody tr:first-of-type td{
   border-top: 1px solid #efefef;
 }
  td img {
    width: 64px;
    height: 64px;
    vertical-align: middle;
  }
  th,td{
    min-width: 150px;
  }
  .orderId {
    height: 30px;
    line-height: 30px;
    text-align: left;
    text-indent: 2em;
    font-size: 12px;
    background: #f1f1f1;
    color: #3c3c3c;
    position: relative;
  }
  .good-item {
    height: 64px;
    line-height: 64px;
  }
 
  .theadsty {
    height: 30px;
    line-height: 30px;
    min-width: 1210px;
  }
  .itemsty {
    padding: 5px 0;
    box-sizing: content-box;
  }
  .theadbtn {
    border: 1px solid #efefef;
  }
  .protitle {
    margin-top: 20px;
  }
  .active {
    color: rgb(51, 135, 254);
  }
  .orderdetail {
    position: absolute;
    right: 20px;
    top: 0;
    line-height: 40px;
  }
  .cancelOrder {
    display: inline-block;
    margin-top: 5px;
    width: 70px;
    text-align: center;
    padding: 3px 1px;
    border: 1px solid #efefef;
  }
  .block {
    padding: 20px;
    float: right;
    box-sizing: border-box;
  }
</style>

