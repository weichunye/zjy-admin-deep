<template>
	<div class="class-detailadd">
    <Heade :activeName="'class'"></Heade>
    <div class="pre-box content">
      <div class="creatClass-dia">
        <el-form ref="form" :model="classForm" label-width="80px">
          <el-form-item label="名称">
            <el-input v-model="classForm.name"></el-input>
          </el-form-item>
          <el-form-item label="封面" prop="pic">
            <el-upload class="upload-demo" action="" :auto-upload='false' :on-change='changeUpload'>
              <el-button size="small" type="primary">点击上传</el-button>
              <div slot="tip" class="el-upload__tip">只能上传jpg/png文件，且不超过500kb</div>
            </el-upload>
          </el-form-item>
          <el-form-item label="课节">
            <el-input-number v-model="classForm.desc" controls-position="right"></el-input-number>
          </el-form-item>
          <el-form-item label="描述" prop="desc1">
            <el-input type="textarea" v-model="classForm.desc1"></el-input>
          </el-form-item>
        </el-form>
      </div>
          <span slot="footer" class="dialog-footer">
        <el-button @click="creatClassVisible = false">取 消</el-button>
        <el-button type="primary" @click="creatClassSuccess">确 定</el-button>
      </span>
    </div>
    <div class="footer"></div>
	</div>
</template>

<script>
import Heade from '../../components/heade.vue'
	export default {
		name: 'Adddetail',
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
          desc:'32',
          region:'bixiu',
          startTime:'2020-02-23',
          desc1:'课程简介课程简介课程简介课程简介课程简介课程简介课程简介课程简介课程简介课\n' +
            '         程简介课程简介课程简介课程简介课程简介课程简介课程简介课程简介课程简介课程简介课程简介课程简介课\n' +
            '         程简介课程简介课程简介'
        },
        addDiscusssVisible:false,
        dialogType:1,
        type: ''
      }
		},
      computed:{

      },
		mounted() {
		},
    created () {
    	this.getParams()
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
        let _this = this
        if(this.type == '编辑') {
        	this.$router.push({
        		path: '/enter',
        		query: {
        		 }
        	})
        } else {
        	this.$router.push({
        		path: '/enter',
        		query: {
        		 classForm: _this.classForm,
        		 }
        	})
        }
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
      },
      getParams(){ // 判断新增还是编辑
      	this.type = this.$route.query.type
      	if(this.type == '编辑') {
      		this.classForm = this.$route.query.classForm
      	} else {
      		this.classForm = {}
      	}
      },
      changeUpload () {}
    }
	}
</script>
<style lang="less">
	.class-detailadd {
    margin-top:70px;
    .footer{
      margin-top:30px;
      height:2px;
      background: #ffffff;
      border-bottom:5px solid #3901b9;
    }
    .content{
      border:1px solid #3901b9;
      background: #ffffff;
      padding-bottom:30px;
      .el-button--primary{
        background-color: #3901b9;
        border-color: #3901b9;
        span{
          color: #ffffff;
        }
      }
      .el-form-item__label{
        text-align: left;
      }
      .el-textarea__inner{
        min-height:100px!important;
      }
      .dialog-footer{
        display: block;
        margin:30px auto;
        text-align: center;
      }
    }
	}
  .creatClass-dia{
    margin: 40px auto;
    //width: 100%;
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
