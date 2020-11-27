<template>
	<div class="resourse-preview">
    <Heade :activeName="'resoure'"></Heade>
    <div class="pre-box content">
      <div class="pre-top">
        <h3>
          {{resourceData.name}}
        </h3>
        <ul>
          <li>
            上传人：周周
          </li>
          <li>
            上传时间： {{resourceData.time}}
          </li>
        </ul>
        <p>资源介绍：{{resourceData.desc}}</p>
      </div>
      <div class="img-box">
        <img   :src="resourceData.img" alt="">
      </div>
    </div>
    <div class="footer">

    </div>
	</div>
</template>

<script>
import Heade from '../../components/heade.vue'
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
        resourceData:''
      }
		},
      computed:{

      },
		mounted() {
      this.resourceData=this.$route.params.resourceData


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
      padding:0 30px;
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
        width:80%;
        overflow: auto;
        margin: 25px auto;
        height: 500px;
        border: 1px solid #b9d7c5;
        img{
          width: 100%;
          height: auto;
        }
      }
      .img-box{
        &::-webkit-scrollbar {/*滚动条整体样式*/
          width: 5px;     /*高宽分别对应横竖滚动条的尺寸*/
          height: 10px;

        }
        &::-webkit-scrollbar-thumb {/*滚动条里面小方块*/

          border-radius: 10px;

          -webkit-box-shadow:none;

          background: #ffffff;

        }

        &::-webkit-scrollbar-track {/*滚动条里面轨道*/

          -webkit-box-shadow:none;

          border-radius: 10px;

          background:#ffffff;

        }
      }
    }
  }

</style>
