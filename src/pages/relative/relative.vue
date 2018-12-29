<template>
    <div>
        <div class="relatvie-title">
            伊利亲属关系
        </div>
        <div class="relative-container">
          <p class="relative-matter">填写注意事项</p>
          <ul class="relative-normlist">
              <li>
                  <h3>若无在伊利工作亲属关系，此项信息无需填写</h3>
              </li>
          </ul>
          <p class="relative-wrtitle">伊利亲属关系填写</p>
          <table class="relative-table" border="1" cellspacing="0">
            <tr>
                <th>与本人关系</th>
                <th>姓名</th>
                <th>联系方式</th>
                <th>所在单位</th>
                <th>职位</th>
                <th>操作</th>
            </tr>
            <tr>
                <td>兄/妹</td>
                <td>小明</td>
                <td>18731973456</td>
                <td>伊利集团</td>
                <td>经理</td>
                <td>
                  <el-button plain size="small"  @click="dialogFormVisible = true">编辑</el-button>
                  <el-button type="danger" size="small"  @click="open2">删除</el-button>
                </td>
            </tr>
          </table>
          <p class="relative-add">
            <el-button type="primary" icon="el-icon-circle-plus-outline" @click="dialogFormVisible = true">添加伊利亲属</el-button>
          </p>
        </div>
        <!--编辑内容-->
        <el-dialog title="伊利亲属关系" :visible.sync="dialogFormVisible">
            <el-form :model="form">
              <el-form-item label="与本人关系" :label-width="formLabelWidth">
                <el-select v-model="form.relative" placeholder="请选择">
                  <el-option
                    v-for="item in relationlist"
                    :key="item.value"
                    :label="item.label"
                    :value="item.value">
                  </el-option>
                </el-select>
              </el-form-item>
              <el-form-item label="姓名" :label-width="formLabelWidth">
                <el-input v-model="form.name" autocomplete="off"></el-input>
              </el-form-item>
              <el-form-item label="联系方式" :label-width="formLabelWidth">
                <el-input v-model="form.phone" autocomplete="off"></el-input>
              </el-form-item>
              <el-form-item label="所在单位" :label-width="formLabelWidth">
                <el-input v-model="form.unit" autocomplete="off"></el-input>
              </el-form-item>
              <el-form-item label="职位" :label-width="formLabelWidth">
                <el-input v-model="form.office" autocomplete="off"></el-input>
              </el-form-item>
            </el-form>
            <div slot="footer" class="dialog-footer">
              <el-button @click="dialogFormVisible = false">取 消</el-button>
              <el-button type="primary" @click="dialogFormVisible = false">确 定</el-button>
            </div>
        </el-dialog>
    </div>
</template>

<script type="text/javascript">
export default{
  name: 'relative',
  data () {
    return {
      dialogTableVisible: false,
      dialogFormVisible: false,
      form: {
        relative: '',
        name: '',
        phone: '',
        unit: '',
        office: ''
      },
      formLabelWidth: '120px',
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
.relatvie-title
  titlebg()
.relative-container
  container()
  .relative-matter
   containertitle()
  .relative-normlist
     margin-top:20px
  .relative-wrtitle
    container_wrtitle()
.relative-table
  container_table()
.relative-table th
  background:#0d6dff
  height:40px
  line-height:40px
  color: #fff
.relative-table th:nth-child(1)
   width:100px
.relative-table th:nth-child(2)
   width:120px
.relative-table th:nth-child(3)
   width:150px
.relative-table th:nth-child(4)
   width:170px
.relative-table th:nth-child(5)
   width:200px
.relative-table td
  background:#e9eef3
  text-align:center
.relative-add
  padding: 10px 20px 10px 0px
  text-align: right
</style>
