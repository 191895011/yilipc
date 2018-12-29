<template>
    <div>
      <div class="job-title">
        历史工作经历
      </div>
       <div class="job-container">
         <p class="job-normtitle">填写注意事项</p>
          <ul class="job-normlist">
            <li>
              <h3>（1）请按照时间倒序（从最近一段工作经历开始）依次填写</h3>
             </li>
            <li>
               <h3>（2）工作经历请按正式开始参加工作（签订劳动合同）的时间填写</h3>
            </li>
            <li>
               <h3>（3）毕业前实习经历小于6个月，无需填写</h3>
            </li>
            <li>
              <h3>（4）若待业情况≧30天，请在原单位处填写“待业”，职位处填写“无”。以保证经历的连续性</h3>
            </li>
            <li>
               <h3>（5）工作单位属于某企业分子公司或分支机构的，需填写所在企业的下设机构名称，如：建设银行内蒙古支行</h3>
            </li>
            <li>
                <h3>（6）以下情况，按如下标准进行填写:</h3>
                <ul class="job-normsecondlist">
                  <li >1.如为个体：请在原单位处填写“个体店名”，职位处填写“个体”。如无店名，请在原单位处填写“无”，职位处填写“个体（行业类别）”</li>
                  <li>2.如为自主创业：单位名称填写“公司名称”，职位填写“自主创业”</li>
                  <li>3.如为农民工/打零工：单位名称填写“无”，职位填写“农民工/打零工”</li>
                  <li>4.如为务农：工作单位填写“无”，职位填写“农民”</li>
                </ul>
            </li>
            <li>
               <h3>（6）联系电话处如为固定电话，格式应为：区号+ 电话号码（例如：04713351234）</h3>
            </li>
          </ul>
          <p class="user-jobtitle">历史工作经历填写</p>
          <table class="job-table" border="1" cellspacing="0">
            <tr>
              <th>开始日期</th>
              <th>结束日期</th>
              <th>原单位</th>
              <th>职位</th>
              <th>证明人</th>
              <th>联系电话</th>
              <th>备注</th>
              <th>操作</th>
            </tr>
            <tr>
              <td>2010-01-01</td>
              <td>2018-01-01</td>
              <td>伊利集团</td>
              <td>经理</td>
              <td>小明</td>
              <td>18932018345</td>
              <td>这是一个备注</td>
              <td>
                <el-button plain size="small" @click="dialogFormVisible = true">编辑</el-button>
                <el-button type="danger" size="small" @click="open2">删除</el-button>
              </td>
            </tr>
            <tr>
              <td>2010-01-01</td>
              <td>2018-01-01</td>
              <td>伊利集团</td>
              <td>经理</td>
              <td>小明</td>
              <td>18932018345</td>
              <td>这是一个备注</td>
              <td>
                <el-button plain size="small" @click="dialogFormVisible = true">编辑</el-button>
                <el-button type="danger" size="small" @click="open2">删除</el-button>
              </td>
            </tr>
          </table>
          <p class="job-adduser">
            <el-button type="primary" icon="el-icon-circle-plus-outline" @click="dialogFormVisible = true">添加工作经历</el-button>
          </p>
          <el-dialog title="历史工作经历" :visible.sync="dialogFormVisible">
            <el-form :model="form">
              <el-form-item label="开始日期" :label-width="formLabelWidth">
                <el-date-picker
                  v-model="form.startTime"
                  type="date"
                  placeholder="选择日期">
                </el-date-picker>
              </el-form-item>
              <el-form-item label="结束日期" :label-width="formLabelWidth">
                <el-date-picker
                  v-model="form.endTime"
                  type="date"
                  placeholder="选择日期">
                </el-date-picker>
              </el-form-item>
              <el-form-item label="职位" :label-width="formLabelWidth">
                <el-input v-model="form.office" autocomplete="off"></el-input>
              </el-form-item>
              <el-form-item label="证明人" :label-width="formLabelWidth">
                <el-input v-model="form.name" autocomplete="off"></el-input>
              </el-form-item>
              <el-form-item label="联系电话" :label-width="formLabelWidth">
                <el-input v-model="form.phone" autocomplete="off"></el-input>
              </el-form-item>
              <el-form-item label="备注" :label-width="formLabelWidth">
                <el-input
                  type="textarea"
                  :rows="2"
                  placeholder="请输入内容"
                  v-model="form.textarea">
                </el-input>
              </el-form-item>
            </el-form>
            <div slot="footer" class="dialog-footer">
              <el-button @click="dialogFormVisible = false">取 消</el-button>
              <el-button type="primary" @click="dialogFormVisible = false">确 定</el-button>
            </div>
          </el-dialog>
       </div>
    </div>
</template>

<script type="text/javascript">
export default {
  name: 'job',
  data () {
    return {
      dialogTableVisible: false,
      dialogFormVisible: false,
      form: {
        startTime: '',
        endTime: '',
        office: '',
        name: '',
        textarea: ''
      },
      formLabelWidth: '120px'
    }
  },
  methods: {
    open2 () {
      this.$confirm('此操作将删除该内容, 是否继续?', '提示', {
        confirmButtonText: '确定',
        cancelButtonText: '取消',
        type: 'warning'
      }).then(() => {
        this.$message({
          type: 'success',
          message: '删除成功!'
        })
      }).catch(() => {
        this.$message({
          type: 'info',
          message: '已取消删除'
        })
      })
    }
  }
}
</script>

<style lang="stylus" scoped>
.job-title
  box-sizing: border-box
  width: 100%
  padding-left: 20px
  background: #0d6dff
  height: 54px
  line-height: 54px
  border: 1px solid #20a0ff
  border-radius: 8px
  font-size: 20px
  color: #fff
  margin-top:20px
.job-container
  box-sizing: border-box
  margin-top: 20px
  padding: 20px
  width: 100%
  background: #fff
  border-radius: 10px
  .job-normtitle
    font-size:16px
    color:#00f
  .job-normlist
    margin-top:20px
  .job-normlist>li
    margin-top:5px
    .job-normsecondlist
      font-size:14px
      padding-left:20px
    .job-normsecondlist>li
      padding-top:5px
  .user-jobtitle
    font-size: 14px
    font-weight: bold
    line-height: 40px
    border-bottom: 1px solid #ffc0cb
  .job-table
    box-sizing:border-box
    margin-top:20px
    width:960px
    border-collapse: collapse
    border:1px solid #fff
  .job-table th
    background:#0d6dff
    height:40px
    line-height:40px
    color: #fff
  .job-table th:nth-child(1)
    width:100px
  .job-table th:nth-child(2)
    width:100px
  .job-table th:nth-child(3)
    width:120px
  .job-table th:nth-child(4)
    width:100px
  .job-table th:nth-child(5)
    width:120px
  .job-table th:nth-child(6)
    width:150px
  .job-table th:nth-child(7)
    width:120px
  .job-table th:nth-child(8)
    width:140px
  .job-table td
    background:#e9eef3
    text-align:center
    height:40px
    line-height:40px
  .job-adduser
     padding:10px 20px 10px 0px
     text-align:right
</style>
