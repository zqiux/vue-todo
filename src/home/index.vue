<template>
  <el-main>
    <el-row type="flex" :gutter="20">
      <el-col :span="8">
        <h4>Add Form</h4>
        <add-form></add-form>
      </el-col>
      <el-col :span="8">
        <h4>Todo List</h4>
      </el-col>
      <el-col :span="8">
        <h4>Done List</h4>
      </el-col>
    </el-row>
    <!-- 按钮 -->
    <el-row type="flex" justify="center" style="margin-top:8px">
      <el-button type="danger">Clear All</el-button>
    </el-row>
    <!-- 下拉选框 -->
    <el-row type="flex" justify="center" align="middle" style="margin-top: 8px;">
      <span>Check Interval:</span>
      <el-select>
          <el-option>

          </el-option>
      </el-select>
    </el-row>
  </el-main>
</template>