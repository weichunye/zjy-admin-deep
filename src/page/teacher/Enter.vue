<template>
	<div class="enter">
    <Heade :activeName="'class'"></Heade>
    <div class="pre-box content">
      <el-row>
        <el-col :span="24">
          <router-link  :to="{path:'/adddetail',query:{type: '新增'}}" >
            <button class="btn-creat-class">新增课程</button>
          </router-link>
        </el-col>
      </el-row>
      <el-row :gutter="20" class="row-content">
        <el-col v-for="item in dataList" :span="8">
          <router-link :to="{name:'ClassDetail',params:{resourceData:item}}">
          <dl style="height: 346px;">
            <dt>
              <img :src="item.img" alt="">
            </dt>
            <dd>
              <h4>
                {{item.name}}
              </h4>
              <p>
                课节:{{item.desc}}节
              </p>
              <p>
                {{item.desc1}}
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
<!--              value-format="yyyy-MM-dd"-->
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
    <div class="footer">

    </div>
	</div>
</template>

<script>
import Heade from '../../components/heade.vue'
	export default {
		name: 'Enter',
		components: {
      Heade


		},
		data() {
			return {
        creatClassVisible:false,
        dataList:[
          {name:'电路',desc:"12",desc1:"电路课程是电工类及电子信息类专业的一门重要的技术基础课",img:'//edu-image.nosdn.127.net/607D19F93EEBE2BD1493A8AB359CF2ED.jpg?imageView&quality=100&thumbnail=230y130&type=webp'},
          {name:'人工智能概论',desc:"24",desc1:"智创未来，未来已来。这是一个人工智能的时代",img:'//edu-image.nosdn.127.net/1CB1B73A8A8347E19E69A4FB839F0162.jpg?imageView&quality=100&thumbnail=230y130&type=webp'},
          {name:'《红楼梦》经典章回评讲',desc:"12",desc1:"十八世纪中叶，一位名为爱新觉罗·永忠的早期红迷，曾高度赞扬《红楼梦》：“传神文笔足千秋，不是情人不泪流",img:'//edu-image.nosdn.127.net/60ACB02668D9FA965151A65F2A8087C7.jpeg?imageView&quality=100&thumbnail=230y130&type=webp'},
          {name:'灵感捕手：设计的创意狂想',desc:"16",desc1:"这是一门会令你脑洞大开的课程，这是一门会让你觉得不可思议的课程，这是一门让你换个角度看世界的课程，原来创意",img:'//edu-image.nosdn.127.net/069B31E2B28F53E57630501EF10F6754.jpg?imageView&quality=100&thumbnail=230y130&type=webp'},
          {name:'Power Electronics',desc:"14",desc1:"For power electronics, it can be seen as the muscle in modern technology and human society. Thus, how to",img:'//edu-image.nosdn.127.net/d9084f0b7bd344219cfcfbe2084dbfec.png?imageView&quality=100&thumbnail=230y130&type=webp'},
          {name:'寄生人体的恶魔—医学寄生虫学',desc:"16",desc1:"寄生虫肉眼可见或不可见，可以是嗜血的昆虫蜱虫，致命的蠕虫原虫；可以潜伏人体、劫持人体免疫系统并伺机爆发、甚",img:'//edu-image.nosdn.127.net/F30EC78AEEAD2AF01CAC3E2FFD164E28.png?imageView&quality=100&thumbnail=230y130&type=webp'},
          {name:'计量经济学',desc:"16",desc1:"计量经济学是现代经济学的核心方法论。如果说爱因斯坦用现存最严谨的语言——数学，证明了宇宙的合理性。那么，计",img:'//edu-image.nosdn.127.net/8F7A876429585CE513911FE47FDC532B.jpg?imageView&quality=100&thumbnail=230y130&type=webp'},
        ],
        classForm:{
          name:'',
          time:'',
          region:'bixiu',
          startTime:'',
          desc:'',
          imageUrl:''
        },
        currentPage1: 5,
        currentPage2: 5,
        currentPage3: 5,
        currentPage4: 4
      }
		},
      computed:{

      },
		mounted() {
		},
    created() {
      this.getParams()
    },
		methods: {
      getParams(){
      	// 取到路由带过来的参数
      	const routerParams = this.$route.query.classForm
      	console.log(routerParams)
      	// 将数据放在当前组件的数据内
      	if (routerParams != null && routerParams !=undefined && routerParams != {}) {
      		this.dataList.push(routerParams)
      	}
      },
      creatClassSuccess(){
        this.creatClassVisible=false
        this.$message({
          message: '课程创建成功',
          type: 'success'
        });
        let newForm={img:"pic_1.png",name:this.classForm.name,desc:this.classForm.desc,time:this.classForm.startTime}
        this.dataList.push(newForm)
      },
      handleAvatarSuccess(file, fileList) {
        this.fileList = fileList;
        this.$nextTick(
          () => {
            let upload_list_li = document.getElementsByClassName('el-upload-list')[0].children;
            for (let i = 0; i < upload_list_li.length; i++) {
              let li_a = upload_list_li[i];
              let imgElement = document.createElement("img");
              imgElement.setAttribute('src', fileList[i].url);
              imgElement.setAttribute('style', "max-width:50%;padding-left:25%");
              if (li_a.lastElementChild.nodeName !== 'IMG') {
                li_a.appendChild(imgElement);
              }
            }
          });
      },
      handleSizeChange(val) {
        console.log(`每页 ${val} 条`);
      },
      handleCurrentChange(val) {
        console.log(`当前页: ${val}`);
      }
    }
	}
</script>
<style lang="less">
	.enter {
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
      .row-content{
        margin:0 0!important;
        display: block;
        padding:0 10px;
        .el-col-8{
          padding:0 30px!important;
        }
      }
      dl{
        padding:0;
        margin-bottom:20px;
        border:1px solid #3901b9;
        &:hover{
          background: #ffffff;
          box-shadow: 0 4px 5px rgba(57, 1, 185, 0.2);
          dd{
            h4{
              color:#3901b9;
            }
          }
        }
        dt{
          width: 100%;
          height: 220px;
          text-align: center;
          img{
            width: 100%;
            height: 220px;
            display: block;
          }

        }
        dd{
          overflow: hidden;
          padding:14px 10px;
          h4{
            width: 100%;
            font-size: 18px;
            line-height: 30px;
            color: #333;
          }
          p{
            width: 100%;
            font-size: 14px;
            line-height: 24px;
            color: #666;
            :nth-child(2){
              display: -webkit-box;
              -webkit-line-clamp: 2;
              -webkit-box-orient: vertical;
              overflow: hidden;
              text-overflow: ellipsis;
              height:36px;
            }
          }
          span{
            float: right;
            font-size: 12px;
            color: #999;
          }
        }

      }
    }
    .btn-creat-class{
      float: left;
      margin: 10px 10px 30px 40px;
      padding: 7px 15px;
      font-size: 14px;
      color: #3901b9;
      background: #ffffff;
      cursor: pointer;
      //border-radius: 6px;
      border:1px solid #3901b9;
      box-shadow: 0 4px 5px rgba(57, 1, 185, 0.2);
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
  .el-pagination{
    text-align: right;
    padding-right:30px;
    .el-pager li:hover{
      color:#3901b9;
    }
    .el-pager li.active{
      color:#3901b9;
    }
  }
</style>
