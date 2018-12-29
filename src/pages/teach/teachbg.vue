<template>
    <div>
      <div class="teachbg-title">
        教育背景
      </div>
      <div class="teachbg-container">
        <p class="teachbg-matter">填写注意事项</p>
        <ul class="teachbg-normlist">
            <li>
                <h3>（1）请从最高学历开始依次填写至初中；无初中及以上学历的，填写小学学历</h3>
            </li>
            <li>
                <h3>（2）教育经历时间需连续，不得出现时间断档或重叠现象；如同一时间段有多段教育经历，需备注说明</h3>
            </li>
            <li>
                <h3>（3）有复读经历的，若在同一学校，可在同一条经历中填写，但需在“备注”中注明“x年至x年复读”，若在不同学校，则需分开填写；预科学习经历与其后的学习经历分开填写（预科学历填写其后取得的学历，专业不填写，学校名称填写“**学校（预科）”）</h3>
            </li>
            <li>
                <h3>（4）若有第二专业，请填写在学历信息最后一行</h3>
            </li>
            <li>
                <h3>（5）学校名称：初中、高中请从“市”开始填写，例如：呼和浩特市第一中学；中技/中专及以上学历的“学校全称”无需加省市，直接填写学校全称即可，例如：内蒙古大学</h3>
            </li>
            <li>
                <h3>（6）学校类型：如同属于211高等和985高等院校，填写985高等院校</h3>
            </li>
            <li>
                <h3>（7）专业类别：本科及以上学历需填写</h3>
            </li>
            <li>
                <h3>（8）专业：中专、中技、大专及以上学历需填写。职业高中的专业根据实际情况填写，如有专业则填写专业，如无专业则不填写，不能填写为“无”</h3>
            </li>
            <li>
                <h3>（9）学历证书编码：需与毕业证信息一致；大专（含）以上学历填写学历证书编号;学历为大专以下及大专及以上未取得学历证书、学位证书，在此栏处填写“无”</h3>
            </li>
            <li>
                <h3>（10）学位证书编码：需与学位证书信息一致；按照学位证书编号填写;学历为大专以下及大专及以上未取得学历证书、学位证书，在此栏处填写“无”</h3>
            </li>
        </ul>
        <p class="teachbg-wrtitle">教育背景填写</p>
        <table class="teachbg-table" border="1" cellspacing="0">
            <tr>
                <th>学历</th>
                <th>开始时间</th>
                <th>结束时间</th>
                <th>学校名称</th>
                <th>学校类型</th>
                <th>专业类别</th>
                <th>专业</th>
                <th>教育形式</th>
                <th>学历证书编号</th>
                <th>学位证书编号</th>
                <th>操作</th>
            </tr>
            <tr>
                <td>本科</td>
                <td>2012-01-01</td>
                <td>2016-01-01</td>
                <td>北京大学</td>
                <td>普通高等院校</td>
                <td>管理学</td>
                <td>经济管理学</td>
                <td>全日制</td>
                <td>123456789012345678</td>
                <td>140xxxxxxxxx</td>
                <td>
                  <el-button plain size="small" @click="dialogFormVisible = true">编辑</el-button>
                  <el-button type="danger" size="small" @click="open2">删除</el-button>
                </td>
            </tr>
        </table>
         <p class="teachbg-add">
            <el-button type="primary" icon="el-icon-circle-plus-outline" @click="dialogFormVisible = true">添加教育经历</el-button>
          </p>
        <el-dialog title="教育背景" :visible.sync="dialogFormVisible">
            <el-form :model="form">
                <el-form-item label="学历" :label-width="formLabelWidth">
                    <el-select v-model="form.Education" placeholder="请选择">
                            <el-option
                              v-for="item in Educationlist"
                              :key="item.value"
                              :label="item.label"
                              :value="item.value">
                            </el-option>
                    </el-select>
                </el-form-item>
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
                <el-form-item label="学校名称" :label-width="formLabelWidth">
                    <el-input v-model="form.School" autocomplete="off"></el-input>
                </el-form-item>
                <el-form-item label="学校类型" :label-width="formLabelWidth">
                    <el-select v-model="form.SchoolType" placeholder="请选择">
                            <el-option
                              v-for="item in SchoolTypelist"
                              :key="item.value"
                              :label="item.label"
                              :value="item.value">
                            </el-option>
                    </el-select>
                </el-form-item>
                <el-form-item label="专业类别" :label-width="formLabelWidth">
                    <el-select v-model="form.SpecialtyType" placeholder="请选择">
                            <el-option
                              v-for="item in SpecialtyTypelist"
                              :key="item.value"
                              :label="item.label"
                              :value="item.value">
                            </el-option>
                    </el-select>
                </el-form-item>
                <el-form-item label="专业" :label-width="formLabelWidth">
                    <el-input v-model="form.Specialty" autocomplete="off"></el-input>
                </el-form-item>
                <el-form-item label="教育形式" :label-width="formLabelWidth">
                    <el-select v-model="form.Teachmode" placeholder="请选择">
                            <el-option
                              v-for="item in Teachmodelist"
                              :key="item.value"
                              :label="item.label"
                              :value="item.value">
                            </el-option>
                    </el-select>
                </el-form-item>
                <el-form-item label="学历证书编号" :label-width="formLabelWidth">
                    <el-input v-model="form.Diploma" autocomplete="off"></el-input>
                </el-form-item>
                <el-form-item label="学位证书编号" :label-width="formLabelWidth">
                    <el-input v-model="form.degree" autocomplete="off"></el-input>
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
  name: 'teachbg',
  data () {
    return {
      dialogTableVisible: false,
      dialogFormVisible: false,
      form: {
        Education: '',
        startTime: '',
        endTime: '',
        School: '',
        SchoolType: '',
        SpecialtyType: '',
        Specialty: '',
        Teachmode: '',
        Diploma: '',
        degree: ''
      },
      formLabelWidth: '120px',
      Educationlist: [{
        value: '1',
        label: '初中'
      }, {
        value: '2',
        label: '高中'
      }, {
        value: '3',
        label: '高中'
      }, {
        value: '4',
        label: '中技'
      }, {
        value: '5',
        label: '中专'
      }, {
        value: '6',
        label: '大专'
      }, {
        value: '7',
        label: '大学'
      }, {
        value: '8',
        label: '硕士研究生'
      }, {
        value: '9',
        label: '博士研究生'
      }, {
        value: '10',
        label: '博士后'
      }],
      SchoolTypelist: [{
        value: '1',
        label: '985高等学校'
      }, {
        value: '2',
        label: '211高等学校'
      }, {
        value: '3',
        label: '普通高等学校'
      }, {
        value: '4',
        label: '成人高等学校'
      }, {
        value: '5',
        label: '党校'
      }, {
        value: '6',
        label: '专业类院校'
      }, {
        value: '7',
        label: '科研机构'
      }, {
        value: '8',
        label: '网络教育'
      }, {
        value: '9',
        label: '自学考试'
      }, {
        value: '10',
        label: '其他'
      }],
      SpecialtyTypelist: [{
        value: '1',
        label: '哲学'
      }, {
        value: '2',
        label: '经济学'
      }, {
        value: '3',
        label: '法学'
      }, {
        value: '4',
        label: '教育学'
      }, {
        value: '5',
        label: '文学'
      }, {
        value: '6',
        label: '艺术学'
      }, {
        value: '7',
        label: '历史学'
      }, {
        value: '8',
        label: '理学'
      }, {
        value: '9',
        label: '工学'
      }, {
        value: '10',
        label: '农学'
      }, {
        value: '11',
        label: '医学'
      }, {
        value: '12',
        label: '管理学'
      }, {
        value: '13',
        label: '军事学'
      }, {
        value: '14',
        label: '无'
      }],
      Teachmodelist: [{
        value: '1',
        label: '普通全日制'
      }, {
        value: '2',
        label: '在职全脱产'
      }, {
        value: '3',
        label: '在职半脱产'
      }, {
        value: '4',
        label: '在职不脱产'
      }, {
        value: '5',
        label: '远程教育'
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
.teachbg-title
  titlebg()
.teachbg-container
  container()
  .teachbg-matter
    containertitle()
  .teachbg-normlist
    margin-top:20px
  .teachbg-normlist>li
    padding-top:5px
    padding-bottom:5px
  .teachbg-wrtitle
    container_wrtitle()
  .teachbg-table
    container_table()
  .teachbg-table th:nth-child(1)
    width:50px
  .teachbg-table th:nth-child(2)
    width:80px
  .teachbg-table th:nth-child(3)
    width:80px
  .teachbg-table th:nth-child(4)
    width:90px
  .teachbg-table th:nth-child(5)
    width:90px
  .teachbg-table th:nth-child(6)
    width:90px
  .teachbg-table th:nth-child(7)
    width:90px
  .teachbg-table th:nth-child(8)
    width:90px
  .teachbg-table th:nth-child(9)
    width:90px
  .teachbg-table th:nth-child(10)
    width:90px
  .teachbg-table th:nth-child(11)
    width:130px
  .teachbg-table th
    background: #0d6dff
    height: 40px
    line-height: 40px
    color:#fff
  .teachbg-table td
    background: #e9eef3
    text-align: center
    height:40px
    line-height:40px
  .teachbg-add
    padding: 10px 20px 10px 0px
    text-align: right
</style>
