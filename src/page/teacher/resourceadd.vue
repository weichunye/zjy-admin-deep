<template>
	<div class="resourceadd">
    <Heade :activeName="'resoure'"></Heade>
    <div class="pre-box content">
      <div class="creatClass-dia">
        <el-form ref="form" :model="classForm" label-width="160px">
          <el-form-item label="资源名称">
            <el-input v-model="classForm.name"></el-input>
          </el-form-item>
          <el-form-item label="选择文件" prop="pic">
            <el-upload class="upload-demo" action="" :auto-upload='false' :on-change='changeUpload'>
              <el-button size="small" type="primary">点击上传</el-button>
            </el-upload>
          </el-form-item>
          <el-form-item label="是否共享到平台资源库">
            <el-radio v-model="radio" label="1">是</el-radio>
            <el-radio v-model="radio" label="2">否</el-radio>
          </el-form-item>
          <el-form-item label="资源描述" prop="desc">
            <el-input type="textarea" v-model="classForm.desc"></el-input>
          </el-form-item>
        </el-form>
      </div>
      <span slot="footer" class="dialog-footer">
        <el-button @click="creatClassVisible = false">取 消</el-button>
        <el-button type="primary" @click="creatClassSuccess">确 定</el-button>
      </span>
    </div>
    <div class="footer">

    </div>
	</div>
</template>

<script>
import Heade from '../../components/heade.vue'
	export default {
		name: 'Resourceadd',
		components: {
      Heade


		},
		data() {
			return {
        dataList:[
          {type:'1',name:'名称','desc':'简介','desc1':'格式'},
          {type:'2',name:'名称','desc':'简介','desc1':'格式'},
          {type:'1',name:'名称','desc':'简介','desc1':'格式'},
          {type:'3',name:'名称','desc':'简介','desc1':'格式'},
          {type:'1',name:'名称','desc':'简介','desc1':'格式'},

        ],
        creatClassVisible:false,
        classForm:{
          name:'',
          time:'',
          region:'bixiu',
          startTime:'',
          desc:'',
          desc1: '',
          imageUrl:'',

        },
        radio:'1'
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
        this.$message({
          message: '资源添加成功',
          type: 'success'
        })
        let newForm={desc1:this.classForm.desc1,name:this.classForm.name,desc:this.classForm.desc}
        this.$router.push({
        	path: '/resource-teacher',
        	query: {
        	 classForm: newForm,
        	 },
        })
      },
      changeUpload (file) {
        console.log(file.raw.type)
        this.classForm.desc1 = file.raw.type
      }

    }
	}
</script>
<style lang="less">
	.resourceadd{
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
      padding: 10px;
      min-height: 600px;
      background: #fff;
      //border:1px solid #3901b9;
      box-shadow: 0 4px 10px rgba(57,1,158,0.2);
      .el-form-item__label{
        text-align: left;
      }
      .el-button--primary{
        color: #FFF;
        background-color: #3901b9;
        border-color: #3901b9;
        span{
          color: #ffffff;
        }
      }
      .dialog-footer{
        margin:40px auto;
        text-align: center;
        display: flex;
        align-items: center;
        justify-content: center;

        .el-button{
          float:initial;
        }
      }
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
          width: 80%;
          h4{
            //margin-top: 10px;
            padding-left: 4%;
            width: 96%;
            font-size: 18px;
            line-height: 30px;
            color: #333;
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
	}

</style>
