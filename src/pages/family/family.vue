<template>
    <div>
        <div class="family-title">
          家庭情况
        </div>
        <div class="family-container">
           <p class="family-matter">填写注意事项</p>
           <ul class="family-normlist">
             <li>
               <h3>（1）需填写父母、兄弟姐妹、配偶、子女的信息</h3>
             </li>
             <li>
               <h3>（2）至少填写一名紧急联系人，且紧急联系人必须填写联系电话；若家庭成员中无紧急联系人，请在与员工关系处勾选“其他”。联系电话如为固定电话，格式为：区号 + 电话号码（例如：04713351234）</h3>
             </li>
             <li>
               <h3>（3）家庭成员为以下情况，请按如下标准进行填写:</h3>
               <ul class="family-secoendlist">
                 <li>1.如为失业/下岗：工作单位填写“原工作单位：……”，职位填写“失业/下岗”</li>
                 <li>2.如为务农：工作单位填写“无”，职位填写“农民”</li>
                 <li>3.如为个体：工作单位填写“店名/公司名称”，职位填写“个体”；或工作单位填写“无”，职位填写“个体（行业类别）”</li>
                 <li>4.如为学生：工作单位填写“学校名称”，职位填写“学生”；未入学子女：工作单位和职位均填写“无”</li>
                 <li>5.如为退休：工作单位填写“退休前工作单位：……”，职位填写“退休”</li>
                 <li>6.如为无业（如家庭妇女）：工作单位填写“无”，职位填写“家庭妇女”或“无业在家”</li>
                 <li>7.如为农民工/打零工：工作单位填写“无”，职位填写“外出务工/打零工”</li>
                 <li>8.自由职业：工作单位填写“无”，职位填写“自由职业（律师/艺术家等）”</li>
               </ul>
             </li>
             <li>
               <h3>（4）配偶是否有工作：个体/务农/打零工/自由职业/退休/下岗请选“否”</h3>
             </li>
           </ul>
           <p class="family-wrtitle">语言能力填写</p>
           <table class="job-table" border="1" cellspacing="0" v-show="familyActive">
            <tr>
              <th>与本人关系</th>
              <th>姓名</th>
              <th>性别</th>
              <th>出生日期</th>
              <th>工作单位/学习院校</th>
              <th>职位/身份</th>
              <th>住址信息</th>
              <th>紧急联系人</th>
              <th>联系方式</th>
              <th>是否在伊利工作</th>
              <th>员工ID</th>
              <th>配偶是否有工作</th>
              <th>操作</th>
            </tr>
            <tr>
              <td>父</td>
              <td>李大山</td>
              <td>男</td>
              <td>1993-02-01</td>
              <td>伊利集团</td>
              <td>经理</td>
              <td>呼和浩特金川区今三道</td>
              <td>是</td>
              <td>187319644565</td>
              <td>是</td>
              <td>140XXXXXXXXXX</td>
              <td>否</td>
              <td>
                <el-button plain size="small" @click="dialogFormVisible = true">编辑</el-button>
                <el-button type="danger" size="small" @click="open2">删除</el-button>
              </td>
            </tr>
          </table>
          <p class="family-add">
            <el-button type="primary" icon="el-icon-circle-plus-outline" @click="dialogFormVisible = true">添加家庭成员</el-button>
          </p>
            <el-dialog title="家庭成员" :visible.sync="dialogFormVisible">
              <el-form :model="form">
                <el-form-item label="与本人关系" :label-width="formLabelWidth">
                  <el-select v-model="form.relation" placeholder="请选择">
                      <el-option
                        v-for="item in relationlist"
                        :key="item.value"
                        :label="item.label"
                        :value="item.value">
                      </el-option>
                  </el-select>
                </el-form-item>
                <el-form-item label="名称" :label-width="formLabelWidth">
                  <el-input v-model="form.name" autocomplete="off"></el-input>
                </el-form-item>
                <el-form-item label="性别" :label-width="formLabelWidth">
                  <el-select v-model="form.sex" placeholder="请选择">
                      <el-option
                        v-for="item in sexlist"
                        :key="item.value"
                        :label="item.label"
                        :value="item.value">
                      </el-option>
                  </el-select>
                </el-form-item>
                <el-form-item label="出生日期" :label-width="formLabelWidth">
                  <el-date-picker
                    v-model="form.BornTime"
                    type="date"
                    placeholder="选择日期">
                  </el-date-picker>
                </el-form-item>
                <el-form-item label="工作单位/学习院校" :label-width="formLabelWidth">
                  <el-input v-model="form.unit" autocomplete="off"></el-input>
                </el-form-item>
                <el-form-item label="职位/身份" :label-width="formLabelWidth">
                  <el-input v-model="form.office" autocomplete="off"></el-input>
                </el-form-item>
                <el-form-item label="住址信息" :label-width="formLabelWidth">
                  <el-input v-model="form.address" autocomplete="off"></el-input>
                </el-form-item>
                <el-form-item label="紧急联系人" :label-width="formLabelWidth">
                  <el-select v-model="form.urgent" placeholder="请选择">
                      <el-option
                        v-for="item in urgentlist"
                        :key="item.value"
                        :label="item.label"
                        :value="item.value">
                      </el-option>
                  </el-select>
                </el-form-item>
                <el-form-item label="联系方式" :label-width="formLabelWidth">
                  <el-input v-model="form.phone" autocomplete="off"></el-input>
                </el-form-item>
                <el-form-item label="是否在伊利工作" :label-width="formLabelWidth">
                  <el-select v-model="form.yilijob" placeholder="请选择">
                      <el-option
                        v-for="item in urgentlist"
                        :key="item.value"
                        :label="item.label"
                        :value="item.value">
                      </el-option>
                  </el-select>
                </el-form-item>
                <el-form-item label="员工ID" :label-width="formLabelWidth">
                  <el-input v-model="form.ID" autocomplete="off"></el-input>
                </el-form-item>
                <el-form-item label="配偶是否有工作" :label-width="formLabelWidth">
                      <el-select v-model="form.matejob" placeholder="请选择">
                          <el-option
                            v-for="item in urgentlist"
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
export default {
  name: 'family',
  data () {
    return {
      familyActive: true,
      dialogTableVisible: false,
      dialogFormVisible: false,
      form: {
        relation: '',
        name: '',
        sex: '',
        BornTime: '',
        unit: '',
        office: '',
        address: '',
        urgent: '',
        phone: '',
        yilijob: '',
        ID: '',
        matejob: ''
      },
      formLabelWidth: '130px',
      relationlist: [{
        value: '1',
        label: '配偶'
      }, {
        value: '2',
        label: '子'
      }, {
        value: '3',
        label: '女'
      }, {
        value: '4',
        label: '父/母'
      }, {
        value: '5',
        label: '兄/嫂'
      }, {
        value: '6',
        label: '弟/弟媳'
      }, {
        value: '7',
        label: '姐/姐夫'
      }, {
        value: '8',
        label: '妹/妹夫'
      }, {
        value: '9',
        label: '其他'
      }],
      sexlist: [{
        value: '1',
        label: '男'
      }, {
        value: '2',
        label: '女'
      }],
      urgentlist: [{
        value: '1',
        label: '是'
      }, {
        value: '2',
        label: '否'
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
.family-title
  titlebg()
.family-container
  container()
  .family-matter
   containertitle()
  .family-normlist
    margin-top:20px
  .family-normlist>li
    margin-top:5px
    .family-secoendlist
      font-size:14px
      padding-left:20px
    .family-secoendlist>li
      margin-top:5px
.family-wrtitle
  container_wrtitle()
.job-table
  container_table()
.job-table th
    background:#0d6dff
    height:40px
    line-height:40px
    color: #fff
.job-table th:nth-child(1)
    width:85px
  .job-table th:nth-child(2)
    width:65px
  .job-table th:nth-child(3)
    width:65px
  .job-table th:nth-child(4)
    width:70px
  .job-table th:nth-child(5)
    width:100px
  .job-table th:nth-child(6)
    width:90px
  .job-table th:nth-child(7)
    width:80px
  .job-table th:nth-child(8)
    width:90px
  .job-table th:nth-child(9)
    width:90px
  .job-table th:nth-child(10)
    width:90px
  .job-table th:nth-child(11)
    width:90px
  .job-table th:nth-child(12)
    width:90px
  .job-table th:nth-child(13)
    width:150px
  .job-table td
    background:#e9eef3
    text-align:center
  .family-add
    padding: 10px 20px 10px 0px
    text-align: right
</style>
