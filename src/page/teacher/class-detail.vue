<template>
	<div class="class-detail">
    <Heade :activeName="'class'"></Heade>
    <div class="pre-box content">
      <el-tabs type="border-card" style="margin:0 40px;">
        <el-tab-pane>
          <span slot="label"> 课程详情</span>
          <div class="text-box">
            <p>
              <span>课程名称：</span>{{resourceData.name}}
            </p>
            <p>
              <span>课时：</span>{{resourceData.desc}}
            </p>
<!--            <p>-->
<!--              <span>开课日期：</span>2020-02-23-->
<!--            </p>-->
            <p>
              <span >课程封面：</span><img :src="resourceData.img" alt="">
            </p>
<!--            <p>-->
<!--              <span>课程类型：</span>必修-->
<!--            </p>-->
            <p>
              <span>描述：</span>{{resourceData.desc1}}
            </p>
          </div>
          <el-row >
            <el-col :span="24">
              <router-link  :to="{path:'/adddetail', query:{type: '编辑',classForm: classForm}}" >
                <button class="btn-creat-class btn-creat-left">编辑课程</button>
              </router-link>
            </el-col>
          </el-row>
        </el-tab-pane>
        <el-tab-pane label="互动课堂">
          <el-row>
            <el-col :span="24">
              <button class="btn-creat-class" @click="editClassroom(2)">添加互动课堂</button>
            </el-col>
          </el-row>
          <el-row :gutter="20">
            <el-col :span="6" v-for="item of dataList" class="text-wapper">
              <el-card class="box-card" style="height: 158px;">
                <div slot="header" class="clearfix">
                  <span>{{item.name}}</span>
                  <p style="display:inline-block; float:right;text-align: right; color: #999; font-size: 12px">{{item.time}}</p>
                </div>
                <div class="text-item">
                  <p>{{item.desc}}</p>
                </div>
                <div class="text-button">
                  <el-button @click="editClassroom(3, item)" style="float: right; padding: 5px 8px; margin-left: 10px " type="primary" plain >编辑</el-button>
                  <el-button @click="interactionVisible=true" style="float: right;padding: 5px 8px; " type="success" plain>备课</el-button>
                </div>
              </el-card>
            </el-col>
          </el-row>


        </el-tab-pane>
      </el-tabs>
    </div>
    <el-dialog
      title="备课"
      :visible.sync="interactionVisible"
      width="80%"
    >
      <div class="creatClass-dia">
        <el-tabs :tab-position="tabPosition" style="height: 350px;">
          <el-tab-pane label="添加资料">
            <div class="add-data">
              <el-upload class="upload-demo" action="" :auto-upload='false' :on-change='changeZl'>
                <el-button size="small" type="primary">点击上传</el-button>
              </el-upload>
              <div class="li-name" v-for="item of zlList">
                {{item.name}}<span>删除</span>
              </div>
            </div>
          </el-tab-pane>
          <el-tab-pane label="添加作业">
            <div class="add-data">
              <el-upload class="upload-demo" action="" :auto-upload='false' :on-change='changeUpload'>
                <el-button size="small" type="primary">添加作业</el-button>
              </el-upload>
              <div class="li-name" v-for="item of zyList">
                {{item.name}} <span>删除</span>
              </div>
            </div>
          </el-tab-pane>
          <el-tab-pane label="添加活动">
            <div class="add-data">
              <el-row :gutter="20">
                <el-col :span="24">
                  <el-button @click="handleAddActive(1)" size="small" type="primary" style="margin-left:10px;">添加投票</el-button>
                  <el-button @click="handleAddActive(4)" size="small" type="primary">添加讨论</el-button>
                  <el-button @click="handleAddActive(5)" size="small" type="primary">抢答</el-button>
                  <el-button @click="handleAddActive(6)" size="small" type="primary">签到</el-button>
                </el-col>
              </el-row>
              <div class="li-name" v-for="item of tpList">
                {{item.name}} <span>删除</span>
              </div>
            </div>
          </el-tab-pane>
        </el-tabs>
      </div>
      <span slot="footer" class="dialog-footer">
 <!--   <el-button @click="interactionVisible = false">取 消</el-button>
    <el-button type="primary" @click="interactionVisible = false">确 定</el-button>-->
  </span>
    </el-dialog>
    <el-dialog
      :title="dialogType==1?'添加投票':dialogType==2?'添加互动课堂':dialogType==4?'添加讨论':dialogType==5?'抢答':dialogType==6?'签到':'编辑互动课堂'"
      :visible.sync="addDiscusssVisible"
      class="dialog-form"
      width="30%">
      <div class="creatClass-dia">
        <el-form v-if="dialogType==1" ref="form" :model="discussForm" label-width="80px">
          <el-form-item label="投票名称">
            <el-input v-model="discussForm.name"></el-input>
          </el-form-item>
<!--          <el-form-item label="投票描述" prop="desc">-->
<!--            <el-input type="textarea" v-model="discussForm.desc"></el-input>-->
<!--          </el-form-item>-->
          <el-form-item label="投票选项">
            <el-form-item label="选项A" style="margin:5px auto;">
              <el-input v-model="discussForm.optionsA"></el-input>
            </el-form-item>
            <el-form-item label="选项B" style="margin:5px auto;">
              <el-input v-model="discussForm.optionsB"></el-input>
            </el-form-item>
            <el-form-item label="选项C" style="margin:5px auto;">
              <el-input v-model="discussForm.optionsC"></el-input>
            </el-form-item>
          </el-form-item>
        </el-form>

        <el-form v-if="dialogType==4" ref="form" :model="discussaForma" label-width="80px">
          <el-form-item label="讨论名称">
            <el-input v-model="discussaForma.namea"></el-input>
          </el-form-item>
          <el-form-item label="讨论描述" prop="desc">
            <el-input type="textarea" v-model="discussForma.desca"></el-input>
          </el-form-item>
        </el-form>

        <el-form v-if="dialogType==5" ref="form" :model="answerForma" label-width="80px">
          <el-form-item label="抢答课程">
            <el-input v-model="answerForma.namea"></el-input>
          </el-form-item>
        </el-form>

        <el-form v-if="dialogType==6" ref="form" :model="SignForma" label-width="80px">
          <el-form-item label="签到名称">
            <el-input v-model="SignForma.namea"></el-input>
          </el-form-item>
          <el-form-item label="签到地点" prop="desc">
            <el-input type="textarea" v-model="SignForma.desca"></el-input>
          </el-form-item>
        </el-form>

        <el-form v-if="dialogType==2||dialogType==3" ref="form" :model="HudongForm" label-width="80px">
          <el-form-item label="课堂名称">
            <el-input v-model="HudongForm.name"></el-input>
          </el-form-item>
          <el-form-item label="上课时间" prop="desc">
            <el-date-picker
              v-model="HudongForm.startTime"
              type="date"
              format='yyyy-MM-dd'
              value-format="yyyy-MM-dd"
              placeholder="选择日期">
            </el-date-picker>
          </el-form-item>
          <el-form-item label="课堂简介" prop="desc">
            <el-input type="textarea" v-model="discussForm.desc"></el-input>
          </el-form-item>
        </el-form>
      </div>
      <span slot="footer" class="dialog-footer">
    <el-button @click="addDiscusssVisible = false">取 消</el-button>
    <el-button type="primary" @click="creatDiscusssSuccess">确 定</el-button>
  </span>
    </el-dialog>
<!--    <el-dialog-->
<!--      title="新建课程"-->
<!--      :visible.sync="creatClassVisible"-->
<!--      width="80%"-->
<!--      :before-close="handleClose">-->
<!--      <div class="creatClass-dia">-->
<!--        <el-form ref="form" :model="classForm" label-width="80px">-->
<!--          <el-form-item label="课程名称">-->
<!--            <el-input v-model="classForm.name"></el-input>-->
<!--          </el-form-item>-->
<!--          <el-form-item label="课程封面" prop="pic">-->
<!--            <el-upload class="upload-demo" action="" :auto-upload='false' :on-change='changeUpload'>-->
<!--              <el-button size="small" type="primary">点击上传</el-button>-->
<!--              <div slot="tip" class="el-upload__tip">只能上传jpg/png文件，且不超过500kb</div>-->
<!--            </el-upload>-->
<!--          </el-form-item>-->
<!--          <el-form-item label="课时">-->
<!--            <el-input-number v-model="classForm.time" controls-position="right"></el-input-number>-->
<!--          </el-form-item>-->
<!--          <el-form-item label="开课日期">-->
<!--            <el-date-picker-->
<!--              v-model="classForm.startTime"-->
<!--              type="date"-->
<!--              placeholder="选择日期">-->
<!--            </el-date-picker>-->
<!--          </el-form-item>-->
<!--          <el-form-item label="课程类型">-->
<!--            <el-select v-model="classForm.region" placeholder="请选择活动区域">-->
<!--              <el-option label="必须课" value="bixiu"></el-option>-->
<!--              <el-option label="选修课" value="xuanxiu"></el-option>-->
<!--            </el-select>-->
<!--          </el-form-item>-->
<!--          <el-form-item label="课程简介" prop="desc">-->
<!--            <el-input type="textarea" v-model="classForm.desc"></el-input>-->
<!--          </el-form-item>-->
<!--        </el-form>-->
<!--      </div>-->
<!--      <span slot="footer" class="dialog-footer">-->
<!--    <el-button @click="creatClassVisible = false">取 消</el-button>-->
<!--    <el-button type="primary" @click="creatClassSuccess">确 定</el-button>-->
<!--  </span>-->
<!--    </el-dialog>-->
    <div class="footer"></div>
	</div>
</template>

<script>
import Heade from '../../components/heade.vue'
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
          desc:'',
          optionsA:'',
          optionsB:'',
          optionsC:'',
        },
        discussForma:{
          namea:'',
          desca:''
        },
        discussaForma:{
          namea:'',
          desca:''
        },
        SignForma:{
          namea:'',
          desca:''
        },
        answerForma:{
          namea:'',
          desca:''
        },
        HudongForm:{
          name:'',
          startTime:''
        },
        classForm:{
          name:'电路',
          desc:'12',
          img:'//edu-image.nosdn.127.net/607D19F93EEBE2BD1493A8AB359CF2ED.jpg?imageView&quality=100&thumbnail=230y130&type=webp',
          startTime:'2020-02-23',
          desc1:'电路课程是电工类及电子信息类专业的一门重要的技术基础课。本课程讲授电路理论的基础知识和电路分析与计算的基本方法。内容包括：电路基本定律、电路定理、线性电路的基本分析方法、线性动态电路的时域分析法、线性动态电路的复频域分析法、正弦电流电路的稳态分析、非正弦周期电流电路的谐波分析法等。本课程理论严密、逻辑性强、有广阔的工程背景。学习本课程对培养科学思维能力、树立工程观点和提高分析与解决问题的能力有重要的作用。'
        },
        addDiscusssVisible:false,
        dialogType:1,
        tabPosition: 'left',
        radio:1,
        dataList:[ // 互动课堂列表
          {name:'电路',desc:"电路课程是电工类及电子信息类专业的一门重要的技术基础课",time: '2020-01-18'},
          {name:'人工智能概论',desc:"智创未来，未来已来。这是一个人工智能的时代",time: '2020-03-26'},
          {name:'《红楼梦》经典章回评讲',desc:"十八世纪中叶，一位名为爱新觉罗·永忠的早期红迷，曾高度赞扬《红楼梦》：“传神文笔足千秋，不是情人不泪流",time: '2020-04-18'},
          {name:'灵感捕手：设计的创意狂想',desc:"这是一门会令你脑洞大开的课程，这是一门会让你觉得不可思议的课程，这是一门让你换个角度看世界的课程，原来创意",time: '2020-06-14'},
          {name:'寄生人体的恶魔—医学寄生虫学',desc:"寄生虫肉眼可见或不可见，可以是嗜血的昆虫蜱虫，致命的蠕虫原虫；可以潜伏人体、劫持人体免疫系统并伺机爆发、甚",time: '2020-08-06'},
          {name:'计量经济学',desc:"计量经济学是现代经济学的核心方法论。如果说爱因斯坦用现存最严谨的语言——数学，证明了宇宙的合理性。那么，计",time: '2020-10-18'}
        ],
        tabType: '', // 3编辑，2添加
        zlList: [ // 资料列表
          {name:'《中国古代房内考》(高罗佩)扫描版'},
          {name:'《图解经典系列》扫描版'},
          {name:'《小小黑客之路—黑客工具、攻防及防火墙编程入门》'},
        ],
        zyList: [
          {name:'《中国古代房内考》主要内容是什么'},
          {name:'《图解经典系列》主要描述什么'}
        ],
        tpList: [
          {name:'本节最喜欢的任务'},
          {name:'最有特点的地方'}
        ],
        resourceData:''
      }
		},
      computed:{

      },
		mounted() {
      this.resourceData=this.$route.params.resourceData


		},

		methods: {
      creatDiscusssSuccess(){
        this.addDiscusssVisible=false
        // this.$message({
        //   message: this.dialogType==1?'添加投票成功':'添加课堂成功',
        //   type: 'success'
        // });
        this.$notify({
          title: '成功',
          customClass:'classtc',
          message: this.dialogType==1?'添加投票成功 !':this.dialogType==4?'添加讨论成功 !':this.dialogType==5?'抢答编辑成功 !':this.dialogType==6?'签到成功 !':'添加课堂成功 !',
          type: 'success'
        });
        if (this.dialogType==2 && this.tabType == 2) { // 互动课堂添加
          let obj = {name: this.HudongForm.name, time: this.HudongForm.startTime, desc: this.discussForm.desc}
          this.dataList.push(obj)
        } else if (this.dialogType==2 && this.tabType == 2) { // 互动课堂编辑
        } else {
          let obj = {name: this.discussForm.name}
          this.tpList.push(obj)
        }
      },
      handleAddActive(index){
        this.dialogType=index
        this.addDiscusssVisible=true

      },
      creatClassSuccess(){
        this.creatClassVisible=false
        this.$notify({
          title: '成功',
          customClass:'classtc',
          message: '课程编辑成功 !',
          type: 'success'
        });
      },
      //编辑课堂信息
      editClassroom(type,obj){
        this.addDiscusssVisible=true
        this.dialogType=type
        if(type==3){ // 编辑互动课堂
          this.tabType = 3
          this.HudongForm.name=obj.name
          this.HudongForm.startTime=obj.time
          this.discussForm.desc=obj.desc
        }else{ // 添加互动课堂
          this.tabType = 2
          this.HudongForm.name=""
          this.HudongForm.startTime=""
          this.discussForm.desc=''
        }
      },
      changeZl (file) { // 上传资料
        let zlName = file.name
        let obj = {name: zlName}
        this.zlList.push(obj)
      },
      changeUpload (file) {
        let zlName = file.name
        let obj = {name: zlName}
        this.zyList.push(obj)
      }
    }
	}
</script>
<style lang="less">
  .text-item{
    display: -webkit-box;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical;
    overflow: hidden;
    text-overflow: ellipsis;
    height: 36px;
  }
  .text-wapper{
    height: 158px;
    margin-bottom: 20px;
  }
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
      //border:1px solid #3901b9;
      box-shadow: 0 5px 10px rgba(57,1,185,0.2);
      padding-top:30px;
      .el-card{
        border:1px solid #3901b9;
      }
      .el-card__header{
        border:none;
      }
      .el-card__body{
        padding-top:0;
      }
      .text-button{
        text-align: center;
        display: flex;
        align-items: center;
        justify-content: space-between;
        width:100%;
        margin-top:20px;
        .el-button{
          float:initial;
          background:#ffffff;
          border:1px solid #3901b9;
          padding:5px 15px!important;
          margin-left:0!important;
          span{
            color:#000000;
            font-size:13px;
          }
        }
      }
      .el-tabs--border-card>.el-tabs__header{
        background: #ffffff;
        border-bottom:none;
      }
      .is-top{
        margin-bottom:10px;
      }
      .el-tabs--border-card{
        border:none;
        box-shadow: none;
      }
      .el-tabs__nav{
        margin:0 auto;
        text-align: center;
        display: block;
        float:initial;
        .el-tabs__item{
          padding:0 50px!important;
          background:#ffffff ;
          border-color:#ffffff ;
          font-size:18px;
          span{
            color: #000000;
            font-size:18px;
          }
          &:hover{
            span{
              color:#3901b9;
            }
            color:#3901b9;
          }
          &.is-active{
            color:#3901b9;
            span{
              color:#3901b9;
            }
          }
        }
      }
      .text-box{
        margin:20px 40px;
        text-align: center;
        p{
          margin:10px auto;
          width:100%;
          font-size: 14px;
          line-height: 24px;
          span{
            font-weight: normal;
            font-size: 14px;
          }
          img{
            height: 150px;
            display: block;
            margin:0 auto;
            text-align: center;
          }

        }
      }

    }
    .btn-creat-class{
      float: left;
      margin: 10px auto;
      padding: 10px 20px;
      font-size: 16px;
      color: #ffffff;
      background: #3901b9;
      border:1px solid #ffffff;
      cursor: pointer;
      //border-radius: 6px;
      text-align: center;
    }
    .btn-creat-left{
      float: right;
      margin: 10px auto;
      padding: 10px 20px;
      font-size: 16px;
      color: #ffffff;
      background: #3901b9;
      border:1px solid #3901b9;
      cursor: pointer;
      //border-radius: 6px;
      text-align: center;
    }
    .creatClass-dia{
      margin: 10px auto;
      width: 100%;
      min-height: 300px;
      .el-tabs__item.is-left{
        text-align: left;
        padding:20px;
        height:60px;
        line-height: 20px;
        &:hover{
          color:#3901b9;
        }
      }
      .el-tabs__active-bar{
        background-color: #3901b9;
      }
      .el-button--primary{
        background: #3901b9;
        float:right;
        span{
          color:#ffffff;
        }
      }
      .upload-demo{
        float:right;
        float:right;
        float:right;
        float:right;
      }
      .el-tabs__item.is-active{
        color:#3901b9;
      }
      .add-data{
        padding: 10px;
        .li-name{
          margin-top: 15px;
          overflow: hidden;
          height: 60px;
          line-height: 60px;
          border:none;
          background: none;
          border-bottom: 1px solid #ededed;
          border-radius: initial;
          margin-bottom: 16px;
          padding: 0 10px;
          width: 100%;
          box-sizing: border-box;
          //background: #e3f6ea;
          &:hover{
            border-color:#3901b9;
          }
          span{
            float: right;
            margin: 0 10px;
          }
          .el-button--primary{
            background: #3901b9;
            span{
              color:#ffffff;
            }
          }
        }
      }
    }
	}
  .dialog-form{
    .el-form-item__label{
      text-align: center;
    }
    .el-button--primary{
      background: #3901b9;
      span{
        color:#ffffff;
      }
    }
  }
</style>
