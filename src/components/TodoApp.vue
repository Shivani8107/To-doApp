<template>
<div v-bind:style ="{ backgroundColor: color}" class="container" >
    <h2 class="text-center mt-5">My Vue Todo App</h2>
    <!-- </--input--/> -->
    <div class="d-flex">
      <input v-model="task" type="text" placeholder="Enter Text" class="form-control">
      <button @click="submitTask" class="btn btn-warning rounded-0">Submit</button> 
    </div>
    <!----Task Table-->
  <table class="table table-bordered mt-5" >
  <thead>
    <tr>
      <th scope="col">Task</th>
      <th scope="col">Status</th>
      <th scope="col" class="text-center">#</th>
      <th scope="col" class="text-center">#</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="(task, index) in tasks" :key ="index">
      <td>
        <span :class="{'finished' :task.status ==='finished'}">
          {{firstchartoUpper(task.name)}}
        </span>  
      </td>
      <td style="width: 120px">
        <span class="pointer" @click="changeStatus(index)" :class="{'text-danger' :task.status==='to-do','text-warning' :task.status==='in-progress'
        , 'text-success':task.status==='finished'}">
          {{firstchartoUpper(task.status)}}
        </span>
      </td>
      <td>
        <div class="text-center" @click="editTask(index)">
          <span class="fa fa-pen"></span>
        </div>
      </td>
      <td>
        <div class="text-center" @click="deleteTask(index)">
          <span class="fa fa-trash"></span>
        </div>
      </td>
    </tr>
  </tbody>
</table>
  </div>


</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data(){
      return{
        editedTask : null,
        task:'Hello World',
        availableStatus:['to-do','in-progress','finished'],
        tasks: [
        {
          name: 'Create a begginer friendly app',
          status: 'to-do',          
        },
        {
          name: 'Create an advanced level app',
          status: 'in-progress',
        }
        ]

      }
  },
  methods:{
    submitTask(){
      if(this.task.length == 0) return;
      if(this.editedTask==null){
        this.tasks.push({
          name: this.task,
          status:'to-do',
        })
      }
      else{
        this.tasks[this.editedTask].name = this.task,
        this.editedTask = null;
      }
      this.task =''

    },
    deleteTask(index){
      this.tasks.splice(index,1);
    },
    editTask(index){
      this.task = this.tasks[index].name;
      this.editedTask = index
    },
    changeStatus(index){
      let newIndex=this.availableStatus.indexOf(this.tasks[index].status);
      if(++newIndex > 2) newIndex=0;
      this.tasks[index].status = this.availableStatus[newIndex];
    },
    firstchartoUpper(str){
      return str.charAt(0).toUpperCase()+str.slice(1);
    }
  }
}
</script>

<style scoped>
.pointer{
  cursor: pointer;
}   
.finished{
  text-decoration: line-through;
} 
#app{
  color: aquamarine;
}

</style>
