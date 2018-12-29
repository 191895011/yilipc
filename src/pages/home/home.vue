<template>
  <div>
    <el-container>
      <el-header>
         <div class="logoimg">
            <img src="../../assets/images/logo.png" alt="" />
         </div>
          <div class="header-welcome">
            <span class="header-text">欢迎您加入伊利</span>
          </div>
      </el-header>
    </el-container>
    <div class="home-container clearfix">
       <div class="home-center">
          <div class="home-centertop">
          </div>
          <div class="usermsg-title">
             个人信息
          </div>
          <div class="usermsg-form">
            <p class="usermsgnorm">填写注意事项</p>
              <ul class="usernormlist">
                <li>
                  <h3>1.家庭住址:</h3>
                </li>
                <li>
                  <p class="usermsgp">未婚人员指父母的居住地，已婚人员指配偶的居住地；地址需精确到门牌号，如：**小区**号楼/栋**单元**号。（农村地址需具体到村）</p>
                </li>
                <li>
                   <h3>2.户籍地址:</h3>
                </li>
                <li>
                  <p class="usermsgp">指户口薄中“住址”信息（一般户口簿与身份证信息一致，如不一致以户口簿信息为准）；需精确到门牌号，如：**小区**号楼/栋**单元**号。（农村地址需具体到村）</p>
                </li>
                <li>
                  <h3>3.现住址:</h3>
                </li>
                <li>
                  <p class="usermsgp">需精确到门牌号，如：**小区**号楼/栋**单元**号，（农村地址需具体到村）；校招学生可具体到宿舍号，如咸宁西路**号楼**室</p>
                </li>
              </ul>
            <p class="usermsgform">个人信息填写</p>
            <!--form 表单-->
             <div class="form_container">
                <ul>
                  <li class="from_li">
                    <div class="from_left">
                      姓名
                    </div>
                    <div class="from_right">
                      <el-input v-model="user.name" placeholder="请输入内容"></el-input>
                    </div>
                  </li>
                  <li class="from_li">
                    <div class="from_left">
                      国籍
                    </div>
                    <div class="from_right">
                      <el-select v-model="user.container" placeholder="请选择">
                            <el-option
                              v-for="item in container"
                              :key="item.value"
                              :label="item.label"
                              :value="item.value">
                            </el-option>
                        </el-select>
                    </div>
                  </li>
                  <li class="from_li">
                    <div class="from_left">
                      证件类型
                    </div>
                    <div class="from_right">
                      <el-select v-model="user.IDType" placeholder="请选择">
                            <el-option
                              v-for="item in IDTypeList"
                              :key="item.value"
                              :label="item.label"
                              :value="item.value">
                            </el-option>
                        </el-select>
                    </div>
                  </li>
                  <li class="from_li">
                    <div class="from_left">
                      证件号码
                    </div>
                    <div class="from_right">
                      <el-input v-model="user.ID" placeholder="请输入内容"></el-input>
                    </div>
                  </li>
                  <li class="from_li">
                    <div class="from_left">
                      性别
                    </div>
                    <div class="from_right">
                        <el-select v-model="user.sex" placeholder="请选择">
                            <el-option
                              v-for="item in usersexlist"
                              :key="item.value"
                              :label="item.label"
                              :value="item.value">
                            </el-option>
                        </el-select>
                    </div>
                  </li>
                  <li class="from_li">
                    <div class="from_left">
                      出生日期
                    </div>
                    <div class="from_right">
                        <el-date-picker
                          v-model="user.borntime"
                          type="date"
                          placeholder="选择日期">
                        </el-date-picker>
                    </div>
                  </li>
                  <li class="from_li">
                    <div class="from_left">
                      民族
                    </div>
                    <div class="from_right">
                        <el-select v-model="user.race" placeholder="请选择">
                            <el-option
                              v-for="item in userracelist"
                              :key="item.value"
                              :label="item.label"
                              :value="item.value">
                            </el-option>
                        </el-select>
                    </div>
                  </li>
                  <li class="from_li">
                    <div class="from_left">
                      政治面貌
                    </div>
                    <div class="from_right">
                        <el-select v-model="user.Political" placeholder="请选择">
                            <el-option
                              v-for="item in userPoliticallist"
                              :key="item.value"
                              :label="item.label"
                              :value="item.value">
                            </el-option>
                        </el-select>
                    </div>
                  </li>
                  <li class="from_li">
                    <div class="from_left">
                      户口性质
                    </div>
                    <div class="from_right">
                        <el-select v-model="user.Account" placeholder="请选择">
                            <el-option
                              v-for="item in userAccountlist"
                              :key="item.value"
                              :label="item.label"
                              :value="item.value">
                            </el-option>
                        </el-select>
                    </div>
                  </li>
                  <li class="from_li">
                    <div class="from_left">
                      员工是否独生子女
                    </div>
                    <div class="from_right">
                        <el-select v-model="user.Child" placeholder="请选择">
                            <el-option
                              v-for="item in userChildlist"
                              :key="item.value"
                              :label="item.label"
                              :value="item.value">
                            </el-option>
                        </el-select>
                    </div>
                  </li>
                  <li class="from_li">
                    <div class="from_left">
                      籍贯
                    </div>
                    <div class="from_right">
                        <el-input v-model="user.AncestorPlace" placeholder="请输入内容"></el-input>
                    </div>
                  </li>
                  <li class="from_li">
                    <div class="from_left">
                      出生地点
                    </div>
                    <div class="from_right">
                        <el-input v-model="user.Birthplace" placeholder="请输入内容"></el-input>
                    </div>
                  </li>
                  <li class="from_li">
                    <div class="from_left">
                      血型
                    </div>
                    <div class="from_right">
                        <el-select v-model="user.Blood" placeholder="请选择">
                            <el-option
                              v-for="item in userBloodlist"
                              :key="item.value"
                              :label="item.label"
                              :value="item.value">
                            </el-option>
                        </el-select>
                    </div>
                  </li>
                  <li class="from_li">
                    <div class="from_left">
                      身高
                    </div>
                    <div class="from_right">
                        <el-input v-model="user.Height" placeholder="请输入内容"></el-input>
                    </div>
                  </li>
                  <li class="from_li">
                    <div class="from_left">
                      婚姻状况
                    </div>
                    <div class="from_right">
                        <el-select v-model="user.Marriage" placeholder="请选择">
                            <el-option
                              v-for="item in userMarriagelist"
                              :key="item.value"
                              :label="item.label"
                              :value="item.value">
                            </el-option>
                        </el-select>
                    </div>
                  </li>
                  <li class="from_li">
                    <div class="from_left">
                      宗教信仰
                    </div>
                    <div class="from_right">
                        <el-select v-model="user.Religion" placeholder="请选择">
                            <el-option
                              v-for="item in userReligionlist"
                              :key="item.value"
                              :label="item.label"
                              :value="item.value">
                            </el-option>
                        </el-select>
                    </div>
                  </li>
                  <li class="from_li">
                    <div class="from_left">
                      兴趣爱好
                    </div>
                    <div class="from_right">
                        <el-input v-model="user.Savor" placeholder="请输入内容"></el-input>
                    </div>
                  </li>
                  <li class="from_li">
                    <div class="from_left">
                      个人特长
                    </div>
                    <div class="from_right">
                        <el-input v-model="user.Specialty" placeholder="请输入内容"></el-input>
                    </div>
                  </li>
                  <li class="from_li">
                    <div class="from_left">
                      家庭住址
                    </div>
                    <div class="from_right">
                        <el-input v-model="user.FamilyAddress" placeholder="请输入内容"></el-input>
                    </div>
                  </li>
                  <li class="from_li">
                    <div class="from_left">
                    </div>
                    <div class="from_right">
                        <el-input
                          type="textarea"
                          :rows="2"
                          placeholder="请输入详细地址"
                          v-model="textarea">
                        </el-input>
                    </div>
                  </li>
                  <li class="from_li">
                    <div class="from_left">
                      户籍地址
                    </div>
                    <div class="from_right">
                        <el-input v-model="user.CensusAddress" placeholder="请输入内容"></el-input>
                    </div>
                  </li>
                   <li class="from_li">
                    <div class="from_left">
                    </div>
                    <div class="from_right">
                        <el-input
                          type="textarea"
                          :rows="2"
                          placeholder="请输入详细地址"
                          v-model="textarea">
                        </el-input>
                    </div>
                  </li>
                  <li class="from_li">
                    <div class="from_left">
                      现住地址
                    </div>
                    <div class="from_right">
                        <el-input v-model="user.NowAddress" placeholder="请输入内容"></el-input>
                    </div>
                  </li>
                   <li class="from_li">
                    <div class="from_left">
                    </div>
                    <div class="from_right">
                        <el-input
                          type="textarea"
                          :rows="2"
                          placeholder="请输入详细地址"
                          v-model="textarea">
                        </el-input>
                    </div>
                  </li>
                </ul>
             </div>
          </div>
          <!--结束个人信息-->
          <user-job></user-job>
          <!--教育背景-->
          <user-teach></user-teach>
          <!--语言能力-->
          <user-lang></user-lang>
          <!--家庭成员-->
          <user-family></user-family>
          <!--伊利亲属关系-->
          <user-relative></user-relative>
       </div>
    </div>
  </div>
</template>

<script>
import UserJob from '@/pages/job/job'
import UserFamily from '@/pages/family/family'
import UserTeach from '@/pages/teach/teachbg'
import UserLang from '@/pages/language/lang'
import UserRelative from '@/pages/relative/relative'

export default {
  data () {
    return {
      user: {
        name: '',
        sex: '',
        container: '',
        IDType: '',
        ID: '',
        borntime: '',
        race: '',
        AncestorPlace: '',
        Birthplace: '',
        Blood: '',
        Height: '',
        Marriage: '',
        Religion: '',
        Political: '',
        Account: '',
        Child: '',
        Savor: '',
        Specialty: '',
        FamilyAddress: '',
        CensusAddress: '',
        NowAddress: ''
      },
      textarea: '',
      usersexlist: [{
        value: '1',
        label: '男'
      }, {
        value: '2',
        label: '女'
      }],
      userBloodlist: [{
        value: '1',
        label: 'A型'
      }, {
        value: '2',
        label: 'B型'
      }, {
        value: '3',
        label: 'AB型'
      }, {
        value: '4',
        label: 'O型'
      }, {
        value: '5',
        label: '其他'
      }, {
        value: '6',
        label: '不详'
      }],
      container: [{
        value: '1',
        label: '中国'
      }, {
        value: '2',
        label: '美国'
      }, {
        value: '3',
        label: '俄罗斯'
      }, {
        value: '4',
        label: '日本'
      }],
      IDTypeList: [{
        value: '1',
        label: '身份证'
      }, {
        value: '2',
        label: '台胞证'
      }, {
        value: '3',
        label: '港澳通行证'
      }],
      userracelist: [{
        value: '1',
        label: '汉'
      }, {
        value: '2',
        label: '蒙古族'
      }, {
        value: '3',
        label: '满族'
      }, {
        value: '4',
        label: '回族'
      }, {
        value: '5',
        label: '傣族'
      }],
      userMarriagelist: [{
        value: '1',
        label: '已婚'
      }, {
        value: '2',
        label: '未婚'
      }, {
        value: '3',
        label: '离婚'
      }, {
        value: '4',
        label: '丧偶'
      }],
      userReligionlist: [{
        value: '1',
        label: '佛教'
      }, {
        value: '2',
        label: '伊斯兰教'
      }, {
        value: '3',
        label: '基督教'
      }, {
        value: '4',
        label: '道教'
      }],
      userPoliticallist: [{
        value: '1',
        label: '中共党员'
      }, {
        value: '2',
        label: '中共预备党员'
      }, {
        value: '3',
        label: '共青团员'
      }, {
        value: '4',
        label: '群众'
      }, {
        value: '5',
        label: '无党派民主人士'
      }, {
        value: '6',
        label: '九三学社社员'
      }, {
        value: '7',
        label: '农工党党员'
      }, {
        value: '8',
        label: '台盟盟员'
      }, {
        value: '9',
        label: '民建会员'
      }, {
        value: '10',
        label: '民盟盟员'
      }, {
        value: '11',
        label: '民进会员'
      }, {
        value: '12',
        label: '民革会员'
      }, {
        value: '13',
        label: '致公党党员'
      }],
      userAccountlist: [{
        value: '1',
        label: '农业'
      }, {
        value: '2',
        label: '非农'
      }, {
        value: '3',
        label: '台湾籍'
      }],
      userChildlist: [{
        value: '1',
        label: '是'
      }, {
        value: '2',
        label: '否'
      }]
    }
  },
  components: {
    UserJob,
    UserFamily,
    UserTeach,
    UserLang,
    UserRelative
  }
}
</script>
<style lang="stylus" scoped>
.home-container
  width:100%
  background:#E9EEF3
  .home-centertop
    height:20px
  .home-center
    width:1000px
    margin: 0 auto
    background:#e9eef3
    .usermsg-title
      box-sizing: border-box
      width: 100%
      padding-left: 20px
      background: rgb(13,109,255)
      height: 54px
      line-height: 54px
      border: 1px solid #20a0ff
      border-radius: 8px
      font-size: 20px
      color: #fff
    .usermsg-form
      box-sizing: border-box
      margin-top: 20px
      padding: 20px
      width: 100%
      background: #fff
      border-radius: 10px
      .usermsgnorm
        font-size:16px
        color:blue
      .usermsgform
        font-size:14px
        font-weight:bold
        line-height:40px
        border-bottom: 1px solid pink
      .usernormlist
        margin-top:20px
        .usermsgp
           padding-top: 5px
           padding-bottom: 5px
      .form_container
        margin-top:20px
        padding-top:5px
        .from_li
          display:flex
          padding:5px 0px
          .from_left
           flex:1
           font-size:14px
           padding-right:20px
           line-height:40px
           text-align:right
          .from_right
           font-size:14px
           flex:4
</style>
<style type="text/css">
   .el-header{
    background-color: #20a0ff;
    padding: 5px 30px;
    color:#fff;
    display:flex;
  }
  .header-text {
    display:inline-block;
    line-height:50px;
  }
  .logoimg{
    flex:1;
  }
  .header-welcome{
    flex:1;
    font-size:20px;
    font-weight:bold;
  }
</style>
