<template>
    <div class="form">
       <form v-on:submit.prevent="onSubmit">
           <label>Email:</label>
           <input type="email" required v-model="email" placeholder="@email">
           <label>Password</label>
           <input type="password" required v-model="password" placeholder="password">
           <label>Role</label><br>
           <select v-model="role">Select Role
               <option value="Frontend Developer">Frontend Developer</option>
               <option value="Backend Developer">Backend Developer</option>
           </select>
           
           <label>Skills</label>
           <input type="text" v-model="skillName" @keyup="addSkill">
           <div v-for="skill in skills" :key='skill' class="pill">
               {{ skill }}

           </div>
           <button @click="Login">Login</button>
       </form>
    </div>
</template>

<script>
export default {
    name:'Home',
    data() {
        return {
            email:'',
            password: '',
            role:'',
            skillName:' ',
            skills:[]
        }
    },
    methods: {
        addSkill(e){
            if(e.key===',' && this.skillName ){
                this.skills.push(this.skillName)
            }

        }
    },
}
</script>
<style scoped>
form{
    display: inline-block;
    max-width: 700px;
    margin: 30px,auto;
    background: rgb(190, 152, 152);
    /* align-content: center; */
    text-align: left;
    padding: 40px;
    border-radius: 10px;

}
label{
    display: inline-block;
    margin: 25px 0 15px;
    font-size: 0.6em;
    font-weight: bold;
    color: rgb(15, 13, 15);
}
input{
    display:block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;
}
button{
    display:flex;
    margin: 20px 0;
    
}
select{
    display: block;
}

</style>