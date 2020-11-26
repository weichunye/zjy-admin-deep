<template>
  <div class="header-school">
    <ul class="pre-box header-list">
      <li class="logo">
        LOGO
      </li>
      <li class="login">
        <el-dropdown trigger="click">
          <span class="el-dropdown-link">
            花花<span class="span-text">学生</span><i class="el-icon-arrow-down el-icon--right"></i>
          </span>
          <el-dropdown-menu class="dropdom-cont" slot="dropdown"><router-link  :to="{path:'/'}" >
            <el-dropdown-item>退出</el-dropdown-item></router-link>
          </el-dropdown-menu>
        </el-dropdown>
      </li>
      <ul class="text-center">
        <router-link  :to="{path:'/resource-list-s'}" >
        <li :class="[this.activeName=='resoure'?'activename':'']">
          资源列表
        </li>
        </router-link>
        <router-link  :to="{path:'/my-course'}" >
        <li :class="[this.activeName=='class'?'activename':'']">
          我的课程
        </li>
        </router-link>
      </ul>

    </ul>
  </div>
</template>

<script>
  export default {
    name: 'Heade',
    components: {
    },
    props:['activeName'],
    data() {
      return {}
    },
    computed:{

    },
    mounted() {


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
  //.header{
  //  width: 100%;
  //  height: 60px;
  //  background: #21ca65;
  //  .header-list{
  //    margin: 0 auto;
  //    line-height: 60px;
  //    .logo{
  //      float: left;
  //      margin-right: 30px;
  //      margin-left: 0;
  //      font-size: 30px;
  //      color: #fff;
  //    }
  //    li{
  //      float: right;
  //      margin-left: 80px;
  //      padding: 0 10px;
  //      font-size: 20px;
  //      color: #fff;
  //      cursor: pointer;
  //      &:hover{
  //        color: #000;
  //      }
  //    }
  //    .activename{
  //      background: #f6d126;
  //      color: #fff;
  //    }
  //
  //
  //    .login{
  //      font-size: 18px;
  //      color: #fcf5ca;
  //      span{
  //        font-size: 14px;
  //      }
  //      .login-out{
  //        margin-left: 50px;
  //        color: #fff;
  //        padding: 3px 10px;
  //        line-height: 22px;
  //        background: #e9644b;
  //        border-radius: 15px;
  //
  //      }
  //    }
  //  }
  //}
  .header-school{
    width: 100%;
    height:50px;
    background: #ffffff;
    border-top:5px solid #3901b9;
    position: fixed;
    top:0;
    left:0;
    z-index:9;
    box-shadow: 0 5px 20px rgba(57,1,185,0.2);
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

</style>
