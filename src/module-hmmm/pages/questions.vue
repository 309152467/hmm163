<template>
  <div class="app-container">
    <el-card>
      <!-- 按钮 -->
      <div class="btn_box">
        <el-button type="primary">新增试题</el-button>
        <el-button type="success">批量导入</el-button>
      </div>
      <!-- 筛选 -->
      <el-form :model="filterForm" label-width="80px">
        <el-row>
          <el-col :span="6">
            <el-form-item label="学科">
              <!-- label默认宽度是百分百 -->
              <el-input v-model="filterForm.subjectID"></el-input>
            </el-form-item>
          </el-col>
          <el-col :span="6">
            <el-form-item label="学科">
              <!-- label默认宽度是百分百 -->
              <el-input v-model="filterForm.subjectID"></el-input>
            </el-form-item>
          </el-col>
          <el-col :span="6">
            <el-form-item label="学科">
              <!-- label默认宽度是百分百 -->
              <el-input v-model="filterForm.subjectID"></el-input>
            </el-form-item>
          </el-col>
          <el-col :span="6">
            <el-form-item label="学科">
              <!-- label默认宽度是百分百 -->
              <el-input v-model="filterForm.subjectID"></el-input>
            </el-form-item>
          </el-col>
          <el-col :span="6">
            <el-form-item label="学科">
              <!-- label默认宽度是百分百 -->
              <el-input v-model="filterForm.subjectID"></el-input>
            </el-form-item>
          </el-col>
          <el-col :span="6">
            <el-form-item label="学科">
              <!-- label默认宽度是百分百 -->
              <el-input v-model="filterForm.subjectID"></el-input>
            </el-form-item>
          </el-col>
          <el-col :span="6">
            <el-form-item label="学科">
              <!-- label默认宽度是百分百 -->
              <el-input v-model="filterForm.subjectID"></el-input>
            </el-form-item>
          </el-col>
          <el-col :span="6">
            <el-form-item label="学科">
              <!-- label默认宽度是百分百 -->
              <el-input v-model="filterForm.subjectID"></el-input>
            </el-form-item>
          </el-col>
          <el-col :span="6">
            <el-form-item label="学科">
              <!-- label默认宽度是百分百 -->
              <el-input v-model="filterForm.subjectID"></el-input>
            </el-form-item>
          </el-col>
          <el-col :span="6">
            <el-form-item label="学科">
              <!-- label默认宽度是百分百 -->
              <el-input v-model="filterForm.subjectID"></el-input>
            </el-form-item>
          </el-col>
          <el-col :span="6">
            <el-form-item label="学科">
              <!-- label默认宽度是百分百 -->
              <el-input v-model="filterForm.subjectID"></el-input>
            </el-form-item>
          </el-col>

          <el-col :span="6" style="text-align:right">
            <el-button>清除</el-button>
            <el-button type="primary">搜索</el-button>
          </el-col> 
        </el-row>
      </el-form>
      <!-- 列表 --> 
      <!-- data绑定列表数据 -->
      <el-table :data="tableData">
     <el-table-column label="序号">

     </el-table-column>
      </el-table>
      <!-- 分页 -->
    </el-card>
  </div>
</template>
<script>
export default {
  name: 'QuestionsList',
  data() {
    return {
      filterForm: {
        subjectID: null
      },
      // 列表数据 试题列表
      tableData:[]
    }
  }
}
</script>
<style scoped>
.btn_box {
  margin-bottom: 20px;
}
</style>
 