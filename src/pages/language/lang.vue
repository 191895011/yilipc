<template>
  <div>
    <div class="lang-title">
        语言能力
    </div>
    <div class="lang-container">
      <p class="lang-matter">填写注意事项</p>
      <ul class="lang-normlist">
          <li>
              <h3>总成绩未通过及格分不填写</h3>
          </li>
      </ul>
      <p class="lang-wrtitle">语言能力填写</p>
      <table class="lang-table" border="1" cellspacing="0">
          <tr>
              <th>语言</th>
              <th>等级证书</th>
              <th>获证日期</th>
              <th>总成绩</th>
              <th>熟练程度</th>
              <th>操作</th>
          </tr>
          <tr>
              <td>英语</td>
              <td>英语4级</td>
              <td>2018-01-01</td>
              <td>80</td>
              <td>一般</td>
              <td>
                <el-button plain size="small"  @click="dialogFormVisible = true">编辑</el-button>
                <el-button type="danger" size="small" @click="open2">删除</el-button>
              </td>
          </tr>
      </table>
      <p class="lang-add">
            <el-button type="primary" icon="el-icon-circle-plus-outline" @click="dialogFormVisible = true">添加语言能力</el-button>
      </p>
      <el-dialog title="语言能力" :visible.sync="dialogFormVisible">
            <el-form :model="form">
              <el-form-item label="语言" :label-width="formLabelWidth">
                <el-select v-model="form.langType" placeholder="请选择">
                    <el-option
                      v-for="item in langTypelist"
                      :key="item.value"
                      :label="item.label"
                      :value="item.value">
                    </el-option>
                </el-select>
              </el-form-item>
              <el-form-item label="等级证书" :label-width="formLabelWidth">
                <el-select v-model="form.langbook" placeholder="请选择">
                    <el-option
                      v-for="item in langbooklist"
                      :key="item.value"
                      :label="item.label"
                      :value="item.value">
                    </el-option>
                </el-select>
              </el-form-item>
              <el-form-item label="获证日期" :label-width="formLabelWidth">
                <el-date-picker
                  v-model="form.Time"
                  type="date"
                  placeholder="选择日期">
                </el-date-picker>
              </el-form-item>
              <el-form-item label="总成绩" :label-width="formLabelWidth">
                <el-input v-model="form.Grade" autocomplete="off"></el-input>
              </el-form-item>
              <el-form-item label="熟练程度" :label-width="formLabelWidth">
                    <el-select v-model="form.Skilled" placeholder="请选择">
                        <el-option
                          v-for="item in Skilledlist"
                          :key="item.value"
                          :label="item.label"
                          :value="item.value">
                        </el-option>
                    </el-select>
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
export default{
  name: 'lang',
  data () {
    return {
      dialogTableVisible: false,
      dialogFormVisible: false,
      form: {
        langType: '',
        langbook: '',
        Time: '',
        Grade: '',
        Skilled: ''
      },
      formLabelWidth: '120px',
      Skilledlist: [{
        value: '1',
        label: '一般'
      }, {
        value: '2',
        label: '熟练'
      }, {
        value: '3',
        label: '精通'
      }, {
        value: '4',
        label: '良好'
      }],
      langTypelist: [{
        value: '1',
        label: '英语'
      }, {
        value: '2',
        label: '葡萄牙语'
      }, {
        value: '3',
        label: '越语'
      }, {
        value: '4',
        label: '法语'
      }],
      langbooklist: [{
        value: '1',
        label: '英语4级'
      }, {
        value: '2',
        label: '英语6级'
      }, {
        value: '3',
        label: '英语专业4级'
      }, {
        value: '4',
        label: '英语专业8级'
      }]
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
 @import '~@/assets/styles/minsx.styl'
.lang-title
  titlebg()
.lang-container
  container()
  .lang-matter
    containertitle()
  .lang-normlist
    margin-top:20px
  .lang-wrtitle
    container_wrtitle()
  .lang-table
    container_table()
  .lang-table th
    background: #0d6dff
    height: 40px
    line-height: 40px
    color:#fff
  .lang-table th:nth-child(1)
    width:200px
  .lang-table th:nth-child(2)
    width:200px
  .lang-table th:nth-child(3)
    width:100px
  .lang-table th:nth-child(4)
    width:100px
  .lang-table th:nth-child(5)
    width:150px
  .lang-table td
    background: #e9eef3
    text-align: center
    height:40px
    line-height:40px
  .lang-add
    padding: 10px 20px 10px 0px
    text-align: right
</style>
