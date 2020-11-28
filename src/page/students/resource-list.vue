<template>
	<div class="resourse-student">
    <Heade :activeName="'resoure'"></Heade>
    <div class="pre-box content">
      <el-row :gutter="20">
        <el-col :span="8" class="bg-1" v-for="item of dataList">
          <router-link :to="{name:'ResourcePreviewStudents',params:{resourceData:item}}">
          <dl  class="bg">
<!--            <dt>-->
<!--            Word-->
<!--            </dt>-->
            <dd>
              <h4>
                {{item.name}}
              </h4>
              <p>
               {{item.desc}}
              </p>
              <p style="margin-top: 4px">
                预览时间:{{item.prewTime}}
              </p>
            </dd>
        </dl>
          </router-link>
        </el-col>
      </el-row>
      <el-pagination
        @size-change="handleSizeChange"
        @current-change="handleCurrentChange"
        :current-page.sync="currentPage3"
        :page-size="100"
        layout="prev, pager, next, jumper"
        :total="1000">
      </el-pagination>
	</div>
    <div class="footer">

    </div>
  </div>
</template>

<script>
import Heade from '../../components/heade-students.vue'
	export default {
		name: 'ResourseStudent',
		components: {
      Heade


		},
		data() {
			return {
        dataList:[
          {name:'《图解经典系列》扫描版',desc:'图解经典系列是一套图文并茂的图书，该系列对中华经典文化书籍重新进行诠释和解说，通俗易懂，简单实用。',desc1:'pdf','img':require("../../assets/pic/pic_2.jpg"),prewTime:'0时3分12秒'},
          {name:'《小小黑客之路—黑客工具、攻防及防火墙编程入门》',desc:'你推开“黑客”，看见一条路，笑了；他推开“安全”，看见你，也笑了。这就是你的小小黑客之路。','desc1':'pdf','img':require("../../assets/pic/pic_3.jpg"),prewTime:'0时3分12秒'},
          {name:'《20几岁要懂得的社会常识大全集》扫描版','desc':'本书旨在给20几岁的年轻人提供一剂处世良方、一个智慧锦囊，系统介绍了与人相处、识人、社交心理学、人脉，办事、送礼、宴请、潜规则、职场生存、形象、礼仪、口才、沟通、创业、理财、安全等方面的社会常识，针对社会生活中经常要面对的各种情景、事件、场合，深入解析人的微妙心理和复杂的人际关系、社会生活方方面面的各式潜规则、古往今来的老经验，帮助年轻人游刃有余地应对生活、事业中的各种问题。 ','desc1':'pdf','img':require("../../assets/pic/pic_4.jpg"),prewTime:'0时3分12秒'},
          {name:'《心理学专业书籍与资源汇总》','desc':'心理学(Psychology)是研究人和动物心理现象发生、发展和活动规律的一门科学。心理学既研究动物的心理（研究动物心理主要是为了深层次地了解、预测人的心理的发生、发展的规律）也研究人的心理，而以人的心理现象为主要研究对象。 ','desc1':'pdf','img':require("../../assets/pic/pic_5.jpg"),prewTime:'0时3分12秒'},
          {name:'《性学观止（上下册）（插图第6版）》','desc':'美国历史上第一部成功的性学教科书，也是性教育领域的一部经典入门书，被世界多所大学广泛采用为性学课程教材，已被翻译成法语、西班牙语、葡萄牙语、汉语等多种文字。 ','desc1':'pdf','img':require("../../assets/pic/pic_6.jpg"),prewTime:'0时3分12秒'},
          {name:'《超级恋爱催眠术》','desc':'《超级恋爱催眠术》林贞年·催眠图书系列为大众入门类读物，均图文并茂。催眠是作用于无意识的一种技巧，而无意识的力量总是强过意识的力量。 ','desc1':'pdf','img':require("../../assets/pic/pic_7.jpg"),prewTime:'0时3分12秒'},
          {name:'《从零开始学电路基础》资料下载','desc':'《从零开始学电路基础》所介绍的电路基础知识包括：电路的基本定律、定理和基本分析方法，磁场与磁路，交流电路，互感与变压器，电路的过渡过程等内容。 ','desc1':'pdf','img':require("../../assets/pic/pic_8.jpg"),prewTime:'0时3分12秒'},
          {name:'《Excel高级报表宝典》','desc':'本书集中讨论了Excel关于报表开发的所有问题。主要介绍了Excel中最为常用的数据透视表、电子表格报表、参数查询及Web组件等的特点和应用场合及报表开发过程， ','desc1':'pdf','img':require("../../assets/pic/pic_9.jpg"),prewTime:'0时3分12秒'},
          {name:'扫描版《鬼谷子绝学》','desc':'《鬼谷子绝学》一个人缺的永远不是钱，缺的是赚钱的智谋，一个人缺的永远不是团队，缺的是俘获追随者的能力，一个人缺的永远不是人们的爱戴和拥戴，缺的是领导统驭的智慧，本书着重于辩证的实践方法 ','desc1':'pdf','img':require("../../assets/pic/pic_10.jpg"),prewTime:'0时3分12秒'}
      ],
        creatClassVisible:false,
      }
		},
      computed:{

      },
		mounted() {


		},

		methods: {
      creatClassSuccess(){
        let  _this=this
        this.creatClassVisible=false
        this.$notify({
          title: '成功',
          customClass:'classtc',
          message: '资源添加成功!',
          type: 'success'
        });
        let newForm={type:3,name:this.classForm.name,desc:this.classForm.desc}
        _this.dataList.push(newForm)
      },

    }
	}
</script>
<style lang="less">
  .resourse-student {
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
    padding:40px 10px 10px;
    min-height: 600px;
    background: #fff;
    box-shadow: 0 4px 5px rgba(57, 1, 185, 0.2);
    .el-row{
      margin:0 40px!important;
    }
    .bg{
      display: flex;
      align-items: center;
      justify-content: center;
      margin-top:0;
    }
    dl{
      overflow: hidden;
      margin-top: 15px;
      width: 100%;
      height: 87px;
      border-radius: 10px;
      dt{
        float: left;
        //margin-top: 20px;
        width: 50px;
        height: 50px;
        line-height:50px;
        text-align: center;
        font-size: 14px;
        font-weight: bold;
        color: #3901b9;
        //border:1px solid #3901b9;
        background: #fff;
        border-radius: 50%;
      }

      dd{
        float: left;
        width: 100%;
        h4{
          //margin-top: 10px;
          padding-left: 4%;
          width: 96%;
          font-size: 18px;
          line-height: 30px;
          color: #333;
          overflow: hidden;
          text-overflow: ellipsis;
          white-space: nowrap;
        }
        p{
          padding-left: 4%;
          width: 96%;
          font-size: 14px;
          color: #666;
          display: -webkit-box;
          -webkit-line-clamp: 2;
          -webkit-box-orient: vertical;
          overflow: hidden;
          text-overflow: ellipsis;
        }
        span{
          float: right;
          font-size: 12px;
          color: #999;
        }
      }

    }
    .bg-1{
      dt{
        background:#3901b9;
        color:#ffffff ;
      }
    }
    .bg-2{
      dt {
        background:#09b7f8;
        color:#ffffff ;
      }
    }
    .bg-3{
      dt {
        background:#7805b3;
        color:#ffffff ;
      }
    }
    .el-col-8{
      padding:15px 30px 15px!important;
      a{
        border:1px solid #3901b9;
        display: block;
        width:100%;
        padding:10px;
        box-shadow: 0 4px 10px rgba(57,1,158,0.2);
        &:hover{
          background:rgba(57,1,158,0.9);
          h4{
            color:#ffffff;
          }
          p{
            color:#ffffff;
          }
        }
      }
    }
  }
  .btn-creat-class{
    float: left;
    margin: 10px 10px 10px 30px;
    padding: 10px 20px;
    font-size: 16px;
    color: #3901b9;
    background: #ffffff;
    cursor: pointer;
    //border-radius: 6px;
    border:1px solid #3901b9;
  }
  .el-pagination{
    margin-top:100px;
    float:right;
  }
  .creatClass-dia{
    margin: 10px auto;
    width: 100%;
    min-height: 300px;
    .el-textarea__inner{
      height: 150px;
      overflow-y: auto;
    }
    .avatar-uploader .el-upload {
      border: 1px dashed #d9d9d9;
      border-radius: 6px;
      cursor: pointer;
      position: relative;
      overflow: hidden;
    }
    .avatar-uploader .el-upload:hover {
      border-color: #409EFF;
    }
    .avatar-uploader-icon {
      font-size: 28px;
      color: #8c939d;
      width: 178px;
      height: 178px;
      line-height: 178px;
      text-align: center;
    }
    .avatar {
      width: 178px;
      height: 178px;
      display: block;
    }
  }
}
  .creatClass-dia{
    margin: 10px auto;
    width: 90%;
    min-height: 300px;
    .el-textarea__inner{
      height: 150px;
      overflow-y: auto;
    }
    .avatar-uploader .el-upload {
      border: 1px dashed #d9d9d9;
      border-radius: 6px;
      cursor: pointer;
      position: relative;
      overflow: hidden;
    }
    .avatar-uploader .el-upload:hover {
      border-color: #409EFF;
    }
    .avatar-uploader-icon {
      font-size: 28px;
      color: #8c939d;
      width: 178px;
      height: 178px;
      line-height: 178px;
      text-align: center;
    }
    .avatar {
      width: 178px;
      height: 178px;
      display: block;
    }
  }

</style>
