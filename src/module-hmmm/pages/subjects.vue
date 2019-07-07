<template>
  <div class="dashboard-container">
    <!-- 按钮部分 -->
    <el-button type="text" @click="dialogVisible = true">新增学科</el-button>
    <el-dialog title="新增学科" :visible.sync="dialogVisible" width="30%" :before-close="handleClose">
      <el-form  :model="ruleForm">
        <el-form-item label="*学科名称" prop="name">
          <el-input v-model="ruleForm.name"></el-input>
        </el-form-item>
        <el-form-item label="*是否显示" prop="name">
          <el-switch active-color="#13ce66" inactive-color="#ff4949" v-model="value"></el-switch>
        </el-form-item>
      </el-form>
      <span slot="footer" class="dialog-footer">
        <el-button type="primary" @click="dialogVisible = false">确 定</el-button>
        <el-button @click="dialogVisible = false">取 消</el-button>
      </span>
    </el-dialog>

    <!-- 表单部分 -->
    <el-form :inline="true" :model="formInline" class="demo-form-inline">
      <el-form-item label="学科名称" class="el-form-item__label">
        <el-input v-model="formInline.user" placeholder="请输入"></el-input>
      </el-form-item>

      <el-form-item>
        <el-button @click="onClear">清除</el-button>
        <el-button type="primary" :loading="articleLoading" @click="onSubmit">搜索</el-button>
      </el-form-item>
    </el-form>
    <!-- 表格部分 -->
    <el-table :data="articles" style="width: 100%" class="mini">
      <el-table-column prop="id" label="序号" width="100"></el-table-column>
      <el-table-column prop="subjectName" label="学科名称" width="120"></el-table-column>
      <el-table-column prop="creatorID" label="创建者" width="150"></el-table-column>
      <el-table-column prop="addDate" label="创建日期" width="150"></el-table-column>
      <el-table-column prop="isFrontDisplay" label="前台是否显示" width="100"></el-table-column>
      <el-table-column prop="tags" label="二级目录" width="150"></el-table-column>
      <el-table-column prop="totals" label="标签" width="120"></el-table-column>
      <el-table-column prop="twoLevelDirector" label="题目数量" width="120"></el-table-column>
      <el-table-column prop="operation" label="操作" width="300">
        <template slot-scope="scope">
          <el-button type="primary" size="mini" @click="content">二级目录</el-button>
          <el-button type="success" size="mini" @click="tag">学科标签</el-button>
          <el-button type="primary" icon="el-icon-edit" circle @click="scope"></el-button>
          <el-button type="danger" icon="el-icon-delete" circle></el-button>
        </template>
      </el-table-column>
    </el-table>
    <!-- 分页部分 -->
    <el-pagination
      background
      layout="prev, pager, next"
      :total="pages"
      :page-size="1"
      @current-change="pager"
    ></el-pagination>
  </div>
</template>
<script>
import { list } from '@/api/hmmm/subjects'
// import { resolve } from 'url'
export default {
  name: 'SubjectsList',
  data() { 
    return {
       ruleForm: {
          name: ''
      },
      // tableData: [{
      //   number: '',
      //   name: '',
      //   user: '',
      //   data: '',
      //   display: '',
      //   content: '',
      //   label: '',
      //   account: '',
      //   operation: ''
      // }],
      articles: [],
      page: 1,
      pagesize: 1,
      formInline: {
        user: '',
        region: ''
      },
      name: '',
      value: true,
      dialogVisible: false
    }
  },
  created() {
    this.loadArticles()
  },
  methods: {
    onSubmit() {
      this.page = 1
      this.loadArticles()
    },
    async loadArticles() {
      const data = await list()
      this.articles = data.data.items
      console.log(data)
    },
    content() {
      this.$router.push('/subjects/directorys')
    },
    tag() {
      this.$router.push('/subjects/tags')
    },

    pager(newpage) {
      this.page = newpage
      this.loadArticles()
    },
    
    handleClose(done) {
      this.$confirm('确认关闭？')
        .then(_ => {
          done()
        })
        .catch(_ => {})
    }
  }
}
</script>
<style scoped>
.demo-form-inline {
  display: flex;
  justify-content: space-between;
  font-weight: normal;
}
.dashboard-container {
  margin-left: 10px;
}
</style>
