<template>
  <el-main>
    <el-row type="flex" :gutter="20">
      <el-col :span="8">
        <h4>Add Form</h4>
        <add-form @add="handleAddTodo" ref="addForm"></add-form>
      </el-col>
      <el-col :span="8">
        <h4>Todo List</h4>
        <todo-list :todo="todo" ></todo-list>
      </el-col>
      <el-col :span="8">
        <h4>Done List</h4>
        <done-list :done="done"></done-list>
      </el-col>
    </el-row>
    <!-- 按钮 -->
    <el-row type="flex" justify="center" style="margin-top:8px">
      <el-button type="danger" @click="handleClear">Clear All</el-button>
    </el-row>
    <!-- 下拉选框 -->
    <el-row type="flex" justify="center" align="middle" style="margin-top: 8px;">
      <span>Check Interval:</span>
      <el-select placeholder="请选择" v-model="interval">
        <el-option
          v-for="interval in intervalOptions"
          :key="interval.value"
          :label="interval.label"
          :value="interval.value"
        ></el-option>
      </el-select>
    </el-row>
  </el-main>
</template>
<script>
import addForm from "./components/addForm"
import TodoList from "./components/TodoList"
import storage from "../model/storage"
import DoneList from './components/DoneList'


export default {
  name:'home',
  components:{
    addForm,
    TodoList,
    DoneList
  },
  data() {
    return {
      todo:storage.get('todo').value || [],
      done:storage.get('done').value || [],
      interval: "asdf",
      intervalOptions: [
        {
          label: "1 min",
          value: 60000
        },
        {
          label: "3 min",
          value: 180000
        },
        {
          label: "5 min",
          value: 300000
        },
        {
          label: "10 min",
          value: 600000
        },
        {
          label: "15 min",
          value: 900000
        },
        {
          label: "30 min",
          value: 1800000
        }
      ]
    };
  },
  // mounted:function(){
  //   console.log('asd',this.$refs.addForm);
  //   this.$refs.addForm.getMessage('你好吗？')
  // },
  methods:{
    handleAddTodo(payload){
      const newTodo = {...payload,timestamp:Date.now()}
      this.todo.push(newTodo)
      const res = storage.set('todo',JSON.stringify(this.todo))
      if(!res.suc){
        this.$alert(res.msg,'Error')
        .then(function(){})
        .catch(function(){})
      }else{
        this.$MESSAGE({
          message:'Add successfully',
          type:'success'
        })
        this.$refs.addForm.handleResetForm()
      }
    },
    handleClear () {
      this.todo = [];
      this.done = [];
      storage.clear()
    }
    
  }
};
</script>