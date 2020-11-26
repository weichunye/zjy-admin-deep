<template>
	<div class="resourse-preview">
    <Heade :activeName="'resoure'"></Heade>
    <div class="pre-box content">
      <div class="pre-top">
        <h3>
          中国古代房内考》(高罗佩)扫描版
        </h3>
        <ul>
          <li>
            上传人：周周
          </li>
          <li>
            上传时间：2020-03-16
          </li>
        </ul>
        <p>资源介绍：《中国古代房内考》是关于中国古代性文化的专著，在西方汉学界享有盛誉，从根本上影响和改变了西方世界对中国的了解。</p>
        <p>预览时间：0时3分{{prewTime}}秒</p>
      </div>
      <div class="img-box">
        <img src="http://img.xuexi111.org/d/file/kejian/wenxue/2014-12-01/c65a3ae8860d18b6034db55198e59fec.jpg" alt="">
      </div>
    </div>
    <div class="footer">

    </div>
	</div>
</template>

<script>
  import Heade from '../../components/heade-students.vue'
	export default {
		name: 'ResourcePreview',
		components: {
      Heade


		},
		data() {
			return {
        creatClassVisible:false,
        classForm:{
          name:'',
          time:'',
          region:'bixiu',
          startTime:'',
          desc:'',
          imageUrl:'',

        },
        radio:'1',
        prewTime:13
      }
		},
      computed:{

      },
		mounted() {
      setInterval(()=>{
        if(this.prewTime<60){
          this.prewTime=this.prewTime+1
        }else {
          this.prewTime=0
        }

      },1000)


		},

		methods: {
      creatClassSuccess(){
        this.creatClassVisible=false
        this.$message({
          message: '资源添加成功',
          type: 'success'
        });
      },

    }
	}
</script>
<style lang="less">
	.resourse-preview {
    margin-top:70px;
    .footer{
      margin-top:30px;
      height:2px;
      background: #ffffff;
      border-bottom:5px solid #3901b9;
    }
    .content {
      overflow: hidden;
      margin-top: 15px;
      min-height: 600px;
      background: #fff;
      display: flex;
      .pre-top{
        padding: 1% 3%;
        width:17%;
        h3{
          font-size: 20px;
          line-height: 50px;
          color: #000;
          margin:50px 0 30px 0;
        }
        ul{
          overflow: hidden;
          width: 100%;
          li{
            float: initial;
            font-size: 14px;
            line-height: 20px;
            margin:5px 0;
            display: block;
          }
        }
        p{
          width: 100%;
          font-size: 14px;
          line-height: 30px;
        }
      }
      .img-box{
        overflow: auto;
        margin: 25px auto;
        width:80%;
        height: 500px;
        border: 1px solid #b9d7c5;
        img{
          width: 100%;
          height: auto;
        }
      }
    }
  }

</style>
