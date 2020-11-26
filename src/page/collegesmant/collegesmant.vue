
<template>
  <div class="collegesmant">
    <Header :activeName="'collegesmant'"/>
    <div class="pre-box collegesmant-cont">
      <div class="sechinput">
        <el-input v-model="input" placeholder="请输入内容"></el-input>
        <el-button type="primary" icon="el-icon-search">搜索</el-button>
      </div>
      <ul>
        <li v-for="(item, index) of dataList" :key='index' style="height: 160px;">
          <div class="top">
            <h4 class="title">{{item.name}}</h4>
          </div>
          <span class="itemDesc">{{item.desc}}</span>
          <!-- <div class="right">
            <el-button type="text" class="text" v-if="!isAccess" @click="dialogVisible = true">审核</el-button>
            <el-button type="text" v-else disabled>审核</el-button>
            <el-button type="text" class="text" v-if="!isAccess" @click="uploadVisible=true">上传</el-button>
            <el-button type="text" v-else disabled>上传</el-button>
          </div> -->
          <div class="right">
            <el-button  v-if="!item.isAccess"  type="text" class="text" @click="dialogVisible = true,itemNum=index" >审核</el-button>
            <el-button v-else  disabled  type="text">审核</el-button>
            <el-button  v-if="!item.isUpload" type="text" disabled >上传</el-button>
            <el-button  v-else @click="uploadVisible=true,itemNum=index" type="text" class="text">上传</el-button>
          </div>
        </li>
      </ul>
      <el-dialog
        title="审核"
        :visible.sync="dialogVisible"
        class="title-Class"
        width="40%"
        :before-close="handleClose">
        <div class="text">
          <el-form ref="form" :model="classForm" label-width="160px">
            <el-form-item label="审核是否通过">
              <el-radio v-model="radio" label="1">是</el-radio>
              <el-radio v-model="radio" label="0">否</el-radio>
            </el-form-item>
            <el-form-item v-if="radio==0" label="审核意见" prop="desc">
              <el-input type="textarea" v-model="classForm.desc"></el-input>
            </el-form-item>
          </el-form>
        </div>
        <span slot="footer" class="dialog-footer">
                <el-button @click="dialogVisible=false">取消</el-button>
                <el-button type="primary" @click="handleClose">确定</el-button>
              </span>
      </el-dialog>

      <el-dialog
        title="提示"
        :visible.sync="uploadVisible"
        width="30%"
        :before-close="handleClose">
        <span>是否向上共享到平台资源库</span>
        <span slot="footer" class="dialog-footer">
    <el-button @click="uploadVisible = false">取 消</el-button>
    <el-button type="primary" @click="handleUpload">确 定</el-button>
  </span>
      </el-dialog>
    </div>
    <div class="footer"></div>
  </div>
</template>

<script>
  import Header from '@/components/heade.vue'
	export default {
		name: 'Collegesmant',
		components: {
      Header,
		},
		data() {
			return {
        input: '',
        dialogVisible:false,
        radio:'1',
        classForm:{
          desc:''
        },
        isAccess:false,
        uploadVisible:false,
        dataList:[
          {isAccess:false,isUpload: false, time: '2014-07-28',name:'《新概念英语》 1-4册 学生用书','desc':'《新概念英语》（New Concept English）作为享誉全球的最为经典地道的英语教材，以其严密的体系性、严谨的科学性、精湛的实用性、浓郁的趣味性深受英语学习者的青睐。'},
          {isAccess:false,isUpload: true, time: '2012-08-16',name:'《新概念英语语法详解大全》','desc':'本书是专为帮助《新概念英语》的自学者学好语法而编写的。'},
          {isAccess:false,isUpload: false, time: '2016-04-06',name:'考研背单词及重点阅读总汇','desc':'《考研背单词及重点阅读总汇》通过根认识字，提供了超过6000个丰富的英语单词在测试卷的读字真人发音，《考研背单词及重点阅读总汇》集中整理关键词的阅读理解。'},
          {isAccess:false,isUpload: false, time: '2014-09-14',name:'《中华经典藏书(套装共50册)》','desc':'《中华经典藏书(套装共50册)》包含：“四书五经”、诸子百家，经典的价值和魅力在流光岁影里永不褪色，先贤圣哲的智慧光芒照耀着我们的现代生活。为在古代经典与现代经验间架起一座沟通的桥梁，中华书局推出“中华经典藏书”丛书。'}
        ],
      }
		},
      computed:{

      },
		mounted() {


		},
		methods: {
      // handleClose() {
      //   this.dialogVisible=false
      //   this.isAccess=true
      //   this.$message({
      //     message: '审核完成',
      //     type: 'success'
      //   });
      // },
      // handleUpload(){
      //   this.uploadVisible=false
      //   this.$message({
      //     message: '上传成功',
      //     type: 'success'
      //   });
      // },
      handleClose() {
        this.dialogVisible=false
        this.isAccess=true
        this.$message({
          message: '审核完成',
          type: 'success'
        });
        this.dataList[this.itemNum].isAccess=true
        this.dataList[this.itemNum].isUpload=true

      },
      handleUpload(){
        this.uploadVisible=false
        this.$message({
          message: '上传成功',
          type: 'success'
        });
        this.dataList[this.itemNum].isUpload=false
      },
    }
	}
</script>
<style lang="less">
.itemDesc{
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
  text-overflow: ellipsis;
  height: 54px;
}
.collegesmant{
  //width:100%;
  display: block;
  padding:20px 0 20px 0;
  background: #ffffff;
  margin-top:70px;
  .footer{
    margin-top:30px;
    height:2px;
    background: #ffffff;
    border-bottom:5px solid #3901b9;
  }
  .collegesmant-cont{
    min-height:500px;
    display: block;
    .sechinput{
      display: flex;
      padding:20px 20px;
      width:100%;
      text-align: left;
      justify-content: end;
      .el-input{
        display: block;
        width:30%;
        float:left;
      }
      .el-button{
        float:right;
        margin:0 10px;
        background: #3901b9;
        .el-icon-search{
          color: #ffffff;
        }
        span{
          color: #ffffff;
        }
      }
    }
    ul{
      padding:0 20px;
      li{
        width: 31.8%;
        margin:0 2% 2% 0;
        display: inline-block;
        align-items: center;
        justify-content: center;
        border:1px solid #e3e3e3;
        padding:15px;
        box-sizing: border-box;
        .right{
          margin-top:20px;
          float: right;
          .text{
            span{
              color: #3901b9;
            }
          }
        }
        &.active{
          .top .el-button{
            background: #e3e3e3;
            span{
              color:#B3B3B3;
            }
            &:hover{
              background: #e3e3e3;
              span{
                color:#B3B3B3;
              }
            }
          }
        }
        &:hover{
          border-color:#3621fb;
          box-shadow: 0 18px 30px rgba(54,33,251,.09);
        }
        &:nth-child(3n){
          margin-right:0;
        }
        .top{
          display: flex;
          align-items: center;
          justify-content: space-between;
          margin-bottom:6px;
          line-height: 30px;
          .title{
            font-weight: normal;
            font-size:16px;
            cursor: pointer;
          }
        }
      }
    }
  }
}

</style>
