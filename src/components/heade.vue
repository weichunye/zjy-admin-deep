<template>
  <div class="header-school">
    <!--教师端-->
    <ul v-if="this.activeName=='resoure'||this.activeName=='class'" class="pre-box header-list">
      <li class="logo">
        LOGO<span style="font-size:12px; color:#3901b9;">(第三版)</span>
      </li>
      <li class="login">
        <el-dropdown trigger="click">
          <span class="el-dropdown-link">
            赵立楠<span class="span-text">教师</span><i class="el-icon-arrow-down el-icon--right"></i>
          </span>
          <el-dropdown-menu class="dropdom-cont" slot="dropdown"><router-link  :to="{path:'/'}" >
            <el-dropdown-item>退出</el-dropdown-item></router-link>
          </el-dropdown-menu>
        </el-dropdown>
      </li>
      <ul class="text-center">
<!--        <li @click="openScreen">-->
<!--          投屏-->
<!--        </li>-->
        <router-link  :to="{path:'/resource-teacher'}" >
          <li :class="[this.activeName=='resoure'?'activename':'']">
            资源库
          </li>
        </router-link>
        <router-link  :to="{path:'/enter'}" >
          <li :class="[this.activeName=='class'?'activename':'']">
            教学
          </li>
        </router-link>
      </ul>
    </ul>
    <!--院校管理-->
    <ul v-if="this.activeName=='collegesmant'" class="pre-box header-list">
      <li class="logo">
        LOGO<span style="font-size:12px; color:#3901b9;">(第三版)</span>
      </li>
      <li class="login">
        <el-dropdown trigger="click">
          <span class="el-dropdown-link">
            孙婷婷<span class="span-text">院校管理员</span><i class="el-icon-arrow-down el-icon--right"></i>
          </span>
          <el-dropdown-menu class="dropdom-cont" slot="dropdown"><router-link  :to="{path:'/'}" >
            <el-dropdown-item>退出</el-dropdown-item></router-link>
          </el-dropdown-menu>
        </el-dropdown>
      </li>
      <ul class="text-center">
        <li :class="[this.activeName=='collegesmant'?'activename':'']">
          资源审核
        </li>
      </ul>
    </ul>
    <!--平台管理-->
    <ul v-if="this.activeName=='platformmant'" class="pre-box header-list">
      <li class="logo">
        LOGO<span style="font-size:12px; color:#3901b9;">(第三版)</span>
      </li>
      <li class="login">
        <el-dropdown trigger="click">
          <span class="el-dropdown-link">
            李梓轩<span class="span-text">平台管理员</span><i class="el-icon-arrow-down el-icon--right"></i>
          </span>
          <el-dropdown-menu class="dropdom-cont" slot="dropdown"><router-link  :to="{path:'/'}" >
            <el-dropdown-item>退出</el-dropdown-item></router-link>
          </el-dropdown-menu>
        </el-dropdown>
      </li>
      <ul class="text-center">
        <li :class="[this.activeName=='platformmant'?'activename':'']">
          资源审核
        </li>
      </ul>
    </ul>
    <el-dialog
      title=""
      :visible.sync="screenVisible"
      width="30%">
      <div class="screen-box">
        <img src="../assets/teacher/erweim.png" alt="">
        <p>请用手机扫描二维码</p>
      </div>
    </el-dialog>
  </div>
</template>

<script>
  export default {
    name: 'Heade',
    components: {


    },
    props:['activeName'],

    data() {
      return {
        screenVisible:false
      }
    },
    computed:{


    },
    mounted() {
      console.log("activeName",this.activeName)

    },

    methods: {
      openScreen(){
        this.screenVisible=true
        setTimeout(()=>{
          this.screenVisible=false
        },5000)

      }

    }
  }
</script>
<style lang="less">
  .header-school{
    width: 100%;
    height:50px;
    background: #ffffff;
    border-top:5px solid #3901b9;
    position: fixed;
    top:0;
    left:0;
    z-index:9;
    box-shadow: 0 5px 20px rgba(57,1,185,0.5);
    .header-list{
      margin: 0 auto;
      line-height: 50px;
      padding:0 50px;
      //display: flex;
      //align-items: center;
      //justify-content: space-between;
      .logo{
        float: left;
        margin-right: 30px;
        margin-left: 0;
        font-size: 24px;
        color: #3901b9;
        &:hover{
          &::after{
            opacity: 0;
          }
        }
      }
      .text-center{
        display: inline-block;
        text-align: center;
        margin-left:100px;
      }
      li{
        float: right;
        margin:0 40px;
        padding: 0 10px;
        font-size: 14px;
        color: #000000;
        cursor: pointer;
        position: relative;
        &::after{
          position: absolute;
          left:50%;
          width:4px;
          height:4px;
          background: #3901b9;
          border-radius: 50%;
          margin-left:-2px;
          opacity: 0;
          bottom:5px;
          content:"";
        }
        &:hover{
          color: #3901b9;
          &::after{
            opacity: 1;
          }
        }
      }
      .activename{
        background: #ffffff;
        color: #3901b9;
        &::after{
          opacity: 1;
        }
      }

      .login{
        font-size: 18px;
        color: #fcf5ca;
        margin-right:0;
        &:hover{
          &::after{
            opacity: 0;
          }
        }
        .el-dropdown{
          font-size:12px;
          .span-text{
            color: #3901b9;
            font-size:14px;
            font-weight:400;
            margin:0 5px;
          }
        }
        span{
          font-size: 14px;
        }
        .login-out{
          margin-left: 50px;
          color: #fff;
          padding: 3px 10px;
          line-height: 22px;
          background: #e9644b;
          border-radius: 15px;

        }
      }
    }
    .screen-box{
      width: 100%;
      text-align: center;
      img{
        width: 300px;
        height: 300px;
      }
      p{
        font-size: 16px;
        color: #999;
        line-height: 40px;
        text-align: center;
      }
    }
  }
  .dropdom-cont{
    padding:5px 0;
    .el-dropdown-menu__item{
      line-height: 24px;
      padding:0 25px;
      &:hover{
        background: #ffffff;
        color:#3901b9;
      }
    }
  }

</style>
