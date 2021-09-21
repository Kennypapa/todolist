<template>
  <div>
    <form action="">
      
      <div class="form_wrap" >


  
        <div class="input_c">
          <label for="firstname">Firstname:</label>
          <input type="text" name="firstname" placeholder="E.g Kennypapa" v-model.lazy="profile.firstname"/>
        </div>


        <div class="input_c">
          <label for="Lastname">Lastname:</label>
          <input type="text" name="lastname" placeholder="E.g Joseph" v-model.lazy="profile.lastname"/>
        </div>


        <div class="input_c">
          <label>Country:</label>
          <select v-model="profile.country">
            <option>Nigeria</option>
            <option>Ghana</option>
            <option>Cameroon</option>
          </select>
           
        </div>


        <div class="checkboxes">
          <label>Male:</label>
          <input type="checkbox" v-model="profile.categories" value="Male"/>
          <label>Female:</label>
          <input type="checkbox" v-model="profile.categories" value="Female"/>
        </div>


      </div>
      <!-- <button type="submit">Add Student</button> -->
      <div >
        
        <p>Firstname:{{ profile.firstname }}</p>
        <p>Lastname:{{ profile.lastname }}</p>
        <p>Country:{{ profile.country }}</p>
        <ul>
          <li v-for="(category,index) in profile.categories" :key="index">{{ category }}</li>
        </ul>
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
        categories:[]
      },
    //   students:[]
    }
  },
  methods: {
    
      
  },
  created(){
   
  },

}
</script>


<style scoped>


.form_wrap{
  background: #fff;
  width: 50%;
  height: 300px;
  margin: auto;
  padding: 2em 2em;
  margin-bottom: 2em;
}
.input_c{
  display: flex;
  flex-direction: column;
}
.input_c input{
  padding: 12px 10px;
  border: 2px solid #ff5722;
  width: 87%;
 margin-bottom: 29px;
  border-radius: 4px;
}
.input_c input:focus{
  outline:none;
}
label{
  font-family: sans-serif;
}
.input_c select{
  padding: 1em;
  width: 90%;
  border: 2px solid #ff5722;
  margin-bottom: 1.5em;
}
.input_c select:focus{
  outline: none;
}
.preview{
  background: #fff;
  width: 50%;
  margin: auto;
  padding: 2em 2em;
}
p{ 
  font-family: sans-serif;
  background: rgb(245, 251, 253);
  padding: 1em;
}
</style>
