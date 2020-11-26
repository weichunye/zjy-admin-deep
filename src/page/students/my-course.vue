<template>
	<div class="my-course">
    <Heade :activeName="'class'"></Heade>
    <div class="pre-box content">
      <el-row :gutter="20">
        <el-col :span="8" v-for="item of dataList">
          <router-link  :to="{path:'/class-detail-s',query:{id:'2'}}" >
          <dl>
            <dt>
              <img :src="item.img" alt="">
            </dt>
            <dd>
              <h4>
                {{item.name}}
              </h4>
              <p>
                {{item.desc1}}
              </p>
              <div class="my-press">
                <!--                <el-progress :percentage="92"></el-progress>-->
                <span>学习进度:{{item.proce}}%</span>
                <span>课节:{{item.desc}}课节</span>
              </div>
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
		name: 'Enter',
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
          imageUrl:''
        },
        dataList:[
          {name:'电路',desc:"12",desc1:"电路课程是电工类及电子信息类专业的一门重要的技术基础课",img:'//edu-image.nosdn.127.net/607D19F93EEBE2BD1493A8AB359CF2ED.jpg?imageView&quality=100&thumbnail=230y130&type=webp', proce: '92'},
          {name:'人工智能概论',desc:"24",desc1:"智创未来，未来已来。这是一个人工智能的时代",img:'//edu-image.nosdn.127.net/1CB1B73A8A8347E19E69A4FB839F0162.jpg?imageView&quality=100&thumbnail=230y130&type=webp', proce: '62'},
          {name:'《红楼梦》经典章回评讲',desc:"12",desc1:"十八世纪中叶，一位名为爱新觉罗·永忠的早期红迷，曾高度赞扬《红楼梦》：“传神文笔足千秋，不是情人不泪流",img:'//edu-image.nosdn.127.net/60ACB02668D9FA965151A65F2A8087C7.jpeg?imageView&quality=100&thumbnail=230y130&type=webp', proce: '89'},
          {name:'灵感捕手：设计的创意狂想',desc:"16",desc1:"这是一门会令你脑洞大开的课程，这是一门会让你觉得不可思议的课程，这是一门让你换个角度看世界的课程，原来创意",img:'//edu-image.nosdn.127.net/069B31E2B28F53E57630501EF10F6754.jpg?imageView&quality=100&thumbnail=230y130&type=webp', proce: '76'},
          {name:'Power Electronics',desc:"14",desc1:"For power electronics, it can be seen as the muscle in modern technology and human society. Thus, how to",img:'//edu-image.nosdn.127.net/d9084f0b7bd344219cfcfbe2084dbfec.png?imageView&quality=100&thumbnail=230y130&type=webp', proce: '45'},
          {name:'寄生人体的恶魔—医学寄生虫学',desc:"16",desc1:"寄生虫肉眼可见或不可见，可以是嗜血的昆虫蜱虫，致命的蠕虫原虫；可以潜伏人体、劫持人体免疫系统并伺机爆发、甚",img:'//edu-image.nosdn.127.net/F30EC78AEEAD2AF01CAC3E2FFD164E28.png?imageView&quality=100&thumbnail=230y130&type=webp', proce: '78'},
          {name:'计量经济学',desc:"16",desc1:"计量经济学是现代经济学的核心方法论。如果说爱因斯坦用现存最严谨的语言——数学，证明了宇宙的合理性。那么，计",img:'//edu-image.nosdn.127.net/8F7A876429585CE513911FE47FDC532B.jpg?imageView&quality=100&thumbnail=230y130&type=webp', proce: '88'},
        ],
      }
		},
      computed:{

      },
		mounted() {


		},

		methods: {


    }
	}
</script>
<style lang="less">
	.my-course {
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
      padding: 20px 30px;
      min-height: 600px;
      background: #fff;
      box-shadow: 0 4px 10px rgba(57,1,158,0.2);
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
      .el-col-8{
        padding:0 30px!important;
      }
      .el-progress-bar__inner{
        background: #3901b9;
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
          height: 200px;
          text-align: center;
          img{
            width: 100%;
            height: 200px;
          }

        }
        dd{
          overflow: hidden;
          padding: 10px;
          h4{
            width: 100%;
            font-size: 18px;
            line-height: 30px;
            color: #333;
          }
          p{
            width: 100%;
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
            margin: 5px 0 15px 0;
            font-size: 12px;
            color: #999;
          }
          .my-press{
            display: flex;
            align-items: center;
            justify-content: space-between;
          padding-top: 15px;
            width: 100%;
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
      background: #17ae54;
      cursor: pointer;
      border-radius: 6px;
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
