<template>
  <div>
    <form action="" @submit.prevent="addStudent()">
      <div class="form_wrap" >
        <div class="d-flex justify-content-center osr">
          <h1><i>Online student Registration.ng</i></h1>
        </div>
        <div class="input_c">
          <label for="firstname">Firstname:</label>
          <input type="text" name="firstname" placeholder="E.g Kennypapa" v-model="profile.firstname" autocomplete="none" required/>
          <div class="notify_alert" v-if="profile.firstname.length > 6" v-show="!notify_alert"><b class="al_p">Not more than 6 characters...</b></div>
        </div>
        <div class="input_c">
          <label for="Lastname">Lastname:</label>
          <input type="text" name="lastname" placeholder="E.g Joseph" v-model="profile.lastname" autocomplete="none" required/>
           <div class="notify_alert" v-if="profile.lastname.length > 6" v-show="!notify_alert"><b class="al_p">Not more than 6 characters...</b></div>
        </div>
        <div class="input_c">
          <label>Country:</label>
          <select v-model="profile.country">
            <option>Nigeria</option>
            <option>Ghana</option>
            <option>Cameroon</option>
            <option>France</option>
            <option>Cameroon</option>
          </select>     
        </div>
        <div class="checkboxes">
          <div class="check_b">
            <label>
              Male:
            </label>
            <input type="checkbox" v-model="profile.categories" value="Male" class="check"/>
          </div>
          <div class="check_b">
            <label>
              Female:
            </label>
            <input type="checkbox" v-model="profile.categories" value="Female" class="check"/>
          </div>
        </div>
        <div>
         <button type="submit" class="btn">ADD STUDENT</button>
        </div>
      </div>
      <!-------------Preview---------->
      <div :class="{editing: students == editTodo}" class="preview" v-for="(student, index) in students" :key="index">
        <div class="d-flex justify-content-center sp">
          <h4><i>Student profile...</i></h4>
        </div>
        <button type="button" class="btn-close" aria-label="Close" @click="removeStudent()"></button>
        <p @dblclick="editTodo(students)">
          Firstname:{{ student.firstname }}
        </p>
        <p>
          Lastname:{{ student.lastname }}
        </p>
        <p>
          Country:{{ student.country }}
       </p>
        <ul>
          <li v-for="(category,index) in student.categories" :key="index">{{ category }}</li>
        </ul>
        <div class="d-flex justify-content-end reg">
          <i>Registered</i>
        </div>
      </div>
    
    </form>  
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data(){
    return{
      profile:{
        firstname: "",
        lastname:"",
        country:"",
        categories:[],
        notify_alert:false,
        editedTodo:null,
        editedTodoText:null
      },
      students:[]
    }
  },
  methods: {
    addStudent(){
      this.students.push(this.profile);
      localStorage.setItem('student', JSON.stringify(this.students));
      this.students = JSON.parse(localStorage.getItem('student') || '[]');
    },
    removeStudent(){
      var index = this.students.indexOf(1);
      this.students = JSON.parse(localStorage.getItem('student') || '[]');
      this.students.splice(index, 1);
      localStorage.setItem('student', JSON.stringify(this.students));
    },
    editTodo(students){
      this.editedTodo = students;
      this.editedTodoText = students.text;
    },
    updateTodo(students){
      if(!this.editedTodo){
        return;
      }else if(!students.text){
        this.removeStudent();
      }
      this.editTodo = null;
      students.text = this.editedTodoText.trim();
    }, 
  },
  created(){
    this.students = JSON.parse(localStorage.getItem('student') || '[]');
  }, 
}
</script>

<style scoped>
.editing{
  border: red;
}
.form_wrap{
  background: #fff;
  width: 50%;
  height: auto;
  margin: auto;
  padding: 2em 5em;
  margin-bottom: 2em;
}
.osr h1 i,.sp h4 i,.reg i{
  color: #ff5722;
}
.input_c{
  display: flex;
  flex-direction: column;
  position: relative;
}
.input_c input{
 padding: 9px 10px;
  border: 1px solid #ff5722;
  width: 100%;
 margin-bottom: 29px;
  border-radius: 4px;
  font-size: 19px;
}
.input_c input:focus{
  outline:none;
}
label{
  font-family: sans-serif;
}
.input_c select{
  padding: 1em;
  width: 100%;
  border: 1px solid #ff5722;
  margin-bottom: 1.5em;
  border-right: 17px solid #ff5722;
}
.input_c select:focus{
  outline: none;
}
.preview{
  background: #fff;
  width: 50%;
  margin: auto;
  padding: 2em 2em;
  position: relative;
  margin-bottom: 50px;
}
p{ 
  font-family: sans-serif;
  background: lightblue;
  padding: 1em;
}
.notify_alert{
  width: 87%;
  border-radius: 5px;
    /* height: 20px; */
  background: #ff000033;
  position: absolute;
  top: 83px;
}
.al_p{
  font-size: 15px;
  font-family: sans-serif;
  font-weight: 100;
  color: red;
  padding-left: 11px;

}
.btn{
 padding: 0.7em 43px;
    background: #fff;
    color: #000;
    border: none;
    border-radius: 5px;
    cursor: pointer;
    margin-top: 0.5em;
    border: 1px solid #ff5722;
    transition: .5s;
}
.btn:hover{
  background-color: #ff5722;
  color: #fff;
}
.btn:focus{
  box-shadow: none !important;
}
.checkboxes{
  display: flex;
  width: 100%;
  justify-content: center;
}
.check_b{
  margin-right: 27px;
}
.btn-close{
  float: right;
  position: absolute;
  right: 7px;
  top: 8px;
}



</style>
