<template>
	<div class="login-cont">
    <div class="pre-box content">
      <div class="form-warp">
        <h2>账号登陆</h2>
        <div class="login-box">
          <el-form :model="loginForm" ref="loginForm" label-width="100px" class="demo-dynamic">
            <el-form-item
              :rules="[
      { required: true, message: '请输入用户名', trigger: 'blur' },]"
            >
              <el-input @keyup.enter.native="toLogin('loginForm')" placeholder="请输入用户名" v-model="loginForm.name"></el-input>
            </el-form-item>
            <el-form-item
              :rules="[
      { required: true, message: '请输入密码', trigger: 'blur' },]"
            >
              <el-input @keyup.enter.native="toLogin('loginForm')" placeholder="请输入密码" v-model="loginForm.passWord"></el-input>
            </el-form-item>
          </el-form>
          <div @click="toLogin('loginForm')" class="btn-submit">登 录</div>
        </div>
      </div>
    </div>
	</div>
</template>

<script>
	export default {
		name: 'Login',
		components: {


		},
		data() {
			return {
        loginForm:{
          name:'',
          passWord:''
        }
      }
		},
      computed:{

      },
		mounted() {


		},
		methods: {
      toLogin(formName){
        this.$refs[formName].validate((valid) => {
          if (valid) {
            console.log("this.loginForm.name",this.loginForm.name)
            if(this.loginForm.name=="ls"){
              this.$router.push('/enter');
            }
            if(this.loginForm.name=="xs"){
              this.$router.push('/my-course');
            }
            if(this.loginForm.name=="yx"){
              this.$router.push('/collegesmant');
            }
            if(this.loginForm.name=="pt"){
              this.$router.push('/platformmant');
            }
          } else {
            console.log('error submit!!');
            return false;
          }
        });
      }
    }
	}
</script>
<style lang="less">
	.login-cont {
    background:url("../assets/teacher/logo-bg.jpg")no-repeat;
    background-size:100% 100%;
    overflow: hidden;
    width:100vw;
    height:100vh;
    .content {
      overflow: hidden;
      //margin-top: 15px;
      //min-height: 600px;
      height:100%;
      display: flex;
      align-items: center;
      justify-content: center;
      .form-warp{
        width:434px;
        border:5px solid #3901b9;
        padding:10px;
        background: #ffffff;
        .el-form-item__content{
          margin-left:0!important;
        }
        .el-input__inner{
          border-radius: 0;
        }
      }
      h2{
        margin: 35px 0;
        width: 100%;
        font-size: 26px;
        color: #3901b9;
        text-align: center;
      }
      .login-box{
        margin: 0 auto;
        padding:10px 50px 50px;
        width:80%;
        //height: 200px;
        //background: -moz-linear-gradient(top, #b5cadc 40%, #ccd5dc 100%);
        //background: -webkit-linear-gradient(top,  #b5cadc 40%, #ccd5dc 100%);
        //background: -o-linear-gradient(top,  #b5cadc 40%, #ccd5dc 100%);
        //background: -ms-linear-gradient(top,  #b5cadc 40%, #ccd5dc 100%);
        //background: linear-gradient(top,  #b5cadc 40%, #ccd5dc 100%);
        //border-radius: 15px;

      }
      .btn-submit{
      margin: 50px 0 0 0;
        width: 100%;
        height: 40px;
        line-height: 40px;
        font-size:16px;
        color: #fff;
        text-align: center;
        background: #3901b9;
        //border-radius: 5px;
        cursor: pointer;
      }

    }
  }

</style>
