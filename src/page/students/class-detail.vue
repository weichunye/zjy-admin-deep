<template>
	<div class="class-detail">
    <Heade :activeName="'class'"></Heade>
    <div class="pre-box content">
      <div class="text-box">
        <p>
          <span>名称：</span>电路
        </p>
        <p style="width: 360px; margin:10px auto; overflow:hidden;">
         <span > 学习进度：</span>
          <span>92%</span>
<!--          <span  style="width: 260px; float: left;margin-top: 6px"> <el-progress :percentage="92"></el-progress></span>-->

        </p>
        <p>
          <span>课节：</span>12
        </p>
<!--        <p>-->
<!--          <span>开课日期：</span>2020-02-23-->
<!--        </p>-->
        <p>
          <span style="display:block;">课程封面：</span><img src="//edu-image.nosdn.127.net/607D19F93EEBE2BD1493A8AB359CF2ED.jpg?imageView&quality=100&thumbnail=230y130&type=webp" alt="">
        </p>
<!--        <p>-->
<!--          <span>课程类型：</span>必修-->
<!--        </p>-->
        <p>
          <span>描述：</span>电路课程是电工类及电子信息类专业的一门重要的技术基础课。本课程讲授电路理论的基础知识和电路分析与计算的基本方法。内容包括：电路基本定律、电路定理、线性电路的基本分析方法、线性动态电路的时域分析法、线性动态电路的复频域分析法、正弦电流电路的稳态分析、非正弦周期电流电路的谐波分析法等。本课程理论严密、逻辑性强、有广阔的工程背景。学习本课程对培养科学思维能力、树立工程观点和提高分析与解决问题的能力有重要的作用。
        </p>
      </div>
    </div>
    <div class="footer">

    </div>
	</div>
</template>

<script>
  import Heade from '../../components/heade-students.vue'
	export default {
		name: 'Class-Detail',
		components: {
      Heade
		},
		data() {
			return {
        creatClassVisible:false,
        interactionVisible:false,
        activeHudong:'first',
        discussForm:{
          name:'',
          desc:''
        },
        HudongForm:{
          name:'',
          startTime:''
        },
        classForm:{
          name:'人工智能V1',
          time:'32',
          region:'bixiu',
          startTime:'2020-02-23',
          desc:'课程简介课程简介课程简介课程简介课程简介课程简介课程简介课程简介课程简介课\n' +
            '         程简介课程简介课程简介课程简介课程简介课程简介课程简介课程简介课程简介课程简介课程简介课程简介课\n' +
            '         程简介课程简介课程简介'
        },
        addDiscusssVisible:false,
        dialogType:1
      }
		},
      computed:{

      },
		mounted() {


		},

		methods: {
      creatDiscusssSuccess(){
        this.addDiscusssVisible=false
        this.$message({
          message: this.dialogType==1?'添加讨论成功':'添加课堂成功',
          type: 'success'
        });

      },
      creatClassSuccess(){
        this.creatClassVisible=false
        this.$message({
          message: '课程编辑成功',
          type: 'success'
        });
      },
      //编辑课堂信息
      editClassroom(type){
        this.addDiscusssVisible=true
        this.dialogType=type
        if(type==3){
          this.HudongForm.name="课堂名称"
          this.HudongForm.startTime="2020-05-13"
        }else{
          this.HudongForm.name=""
          this.HudongForm.startTime=""
        }



      }

    }
	}
</script>
<style lang="less">
	.class-detail {
    margin-top:70px;
    .footer{
      margin-top:30px;
      height:2px;
      background: #ffffff;
      border-bottom:5px solid #3901b9;
    }
    .content{
      overflow: hidden;
      margin-top: 15px;
      min-height: 600px;
      background: #fff;
      box-shadow: 0 4px 5px rgba(57, 1, 185, 0.2);
      .el-progress-bar__inner{
        background: #3901b9;
      }
      .text-box{
        margin:40px 0;
        text-align: center;
        p{
          margin: 15px auto;
          width:90%;
          font-size: 14px;
          line-height: 24px;
          span{
            font-weight: normal;
            font-size: 14px;
          }
          img{
            height: 150px;
          }

        }
      }

    }
    .btn-creat-class{
      float: right;
      margin: 10px;
      padding: 10px 20px;
      font-size: 16px;
      color: #fff;
      background: #3901b9;
      cursor: pointer;
      border-radius: 6px;
    }
	}
  .creatClass-dia{
    margin: 10px auto;
    width: 90%;
    min-height: 300px;
   .add-data{
     padding: 10px;
       .li-name{
         margin-top: 15px;
         overflow: hidden;
         height: 60px;
         line-height: 60px;
         border: 1px solid #ededed;
         border-radius: 5px;
         margin-bottom: 16px;
         padding: 0 10px;
         width: 100%;
         box-sizing: border-box;
         background: #e3f6ea;
         span{
           float: right;
           margin: 0 10px;
         }

     }
   }
  }

</style>
