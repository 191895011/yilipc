<template>
  <div>
    <el-container>
      <el-header>
         <div class="logoimg">
            <img src="../assets/images/logo.png" alt="" />
         </div>
          <div class="header-welcome">
            <span class="header-text">欢迎您加入伊利</span>
          </div>
      </el-header>
    </el-container>
    <div class="home-container">
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
            <!--form 表单-->
             <div class="form_container">
                <ul>
                  <li class="from_li">
                    <div class="from_left">
                      姓名
                    </div>
                    <div class="from_right">
                      <el-input v-model="input" placeholder="请输入内容"></el-input>
                    </div>
                  </li>
                </ul>
             </div>
          </div>
       </div>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        user: {
          name: '李四'
        }
      }
    }
  }
</script>
<style lang="stylus" scoped>
.home-container
  width:100%
  height:500px
  background:#E9EEF3
  .home-centertop
    height:20px
  .home-center
    width:1000px
    height:200px
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
      height: 300px
      border-radius: 10px
      .usermsgnorm
        font-size:16px
        color:blue
      .usernormlist
        margin-top:20px
        .usermsgp
           padding-top: 5px
           padding-bottom: 5px
      .form_container
        margin-top:20px
        .from_li
          display:flex
          .from_left
           flex: 3
          .from_right
           flex: 4 

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