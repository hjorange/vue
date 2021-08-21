<template>
  <div id="app">
    <div>
      <span>姓名:</span>
      <input type="text" v-model.trim="name" />
    </div>
    <div>
      <span>年龄:</span>
      <input type="number" v-model.number.trim="age"/>
    </div>
    <div>
      <span>性别:</span>
      <select v-model.trim="sex">
        <option value="男">男</option>
        <option value="女">女</option>
      </select>
    </div>
    <div>
      <button @click="btn">添加/修改</button>
    </div>
    <div>
      <table
        border="1"
        cellpadding="10"
        cellspacing="0"
      >
        <tr>
          <th>序号</th>
          <th>姓名</th>
          <th>年龄</th>
          <th>性别</th>
          <th>操作</th>
        </tr>
        <tr v-for="(obj,index) in arr" :key="index">
          <td>{{obj.id}}</td>
          <td>{{obj.name}}</td>
          <td>{{obj.age}}</td>
          <td>{{obj.sex}}</td>
          <td>
            <button @click="del(index)">删除</button>
            <button @click="bj(obj)">编辑</button>
          </td>
        </tr>
      </table>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      name:'',
      age:'',
      sex:'',
      is:true,
arr:[]
    }
  },

  methods: {
btn(){
if(this.is){
   const id=this.arr.length>0?this.arr[this.arr.length-1].id+1:1
  !this.name||!this.age||!this.age?alert('请输入内容'):this.arr.push({
    id:id,
    name:this.name,
    age:this.age,
    sex:this.sex
})
 }
},
bj(index){
  this.is=!this.is
  console.log(index);

},
del(index){
this.arr.splice(index,1)
}
  }
}
</script>

<style scoped>

</style>
