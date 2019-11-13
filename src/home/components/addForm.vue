<template>
  <el-form
    :model="addForm"
    label-width="100px"
    :rules="addFormRules"
    ref="addForm"
    label-position="left"
  >
    <!-- 输入框 -->
    <el-form-item label="Title" prop="title" required>
      <el-input v-model="addForm.title" clearable placeholder="Todo in short, less than 20"></el-input>
    </el-form-item>
    <!-- 文本区域框 -->
    <el-form-item label="Detail" prop="detail" required>
      <el-input type="textarea" v-model="addForm.detail" :rows="8" resize="none" clearable placeholder="Detail for the todo, less than 100"></el-input>
    </el-form-item>
    <!-- 时间 -->
    <el-form-item label="Deadline" prop="deadline" required>
      <el-date-picker type="datetime" v-model="addForm.deadline" placeholder="Pick deadline" value-format="timestamp" :picker-options="detepickerOptions"></el-date-picker>
    </el-form-item>
    <!-- 按钮 -->
    <el-form-item label-width="0" style="text-align:center;">
      <el-button type="primary" @click="handleSubmitForm">Add</el-button>
      <el-button type="">Reset</el-button>
    </el-form-item>

  </el-form>
</template>

<script>
export default {
  data() {
    return {
      addForm: {
        title: "",
        detail:"",
        deadline:""
      },
      addFormRules: {
        title: [
          { required: true, message: "Please set todo title", trigger: "blur" },
          { max: 20, message: "Should less than 20", trigger: "blur" }
        ],
        detail:[
          { required:true,message:'Please set todo detail', trigger:'change' },
          {max:100,message:'Should less than 100', trigger:'blur'}
        ],
        deadline: [
          { type: 'date', required: true, message: 'Please set deadline', trigger: 'change' }
        ]
      },
      detepickerOptions:{
        disabledDate(time){
          return time.getTime() > Date.now();
        }
      }
    }
  },
  methods:{
    handleSubmitForm(){
      this.
    }
  }
};
</script>