<template>
  <div>
  <div class="container mt-5">
      
     <div class="mb-3">

<p class="text-danger" v-text="errors.faculty_number"></p>
    <label for="exampleInputEmail1" class="form-label">ID NUMBER</label>
    <br> 
    
    
    <input type="text" class=" text-line" name="faculty_number"   required aria-describedby="emailHelp"  v-model="formData.faculty_number" placeholder="FAC-001">
<p> <span v-if="v$.formData.faculty_number.$error">{{v$.formData.faculty_number.$errors[0].$message}}</span> </p>
  </div>
  <div class="mb-3">
    <label for="exampleInputPassword1" class="form-label">PASSWORD</label>
    <br>
      <p class="text-danger" v-text="errors.password"></p>
    
    <input type="password" class=" text-line" id="exampleInputPassword1"    required="required" v-model="formData.password" placeholder="FacultyPassword">
   <p> <span v-if="v$.formData.password.$error">{{v$.formData.password.$errors[0].$message}}</span></p>
    
  </div>
  <div class="mb-3 form-check">
    <input type="checkbox" class="form-check-input checkbox-circle" id="exampleCheck1" >
    <label class="form-check-label" for="exampleCheck1">Remember my password</label>
  </div>
   <button  type="submit" @click="login" class="loginbtn mt-5">LOG IN</button>



      </div>
</div>
</template>

<script>

import axios from 'axios'
import useVuelidate from '@vuelidate/core'
import { required } from '@vuelidate/validators'

axios.defaults.withCredentials = true
axios.defaults.baseURL = "http://127.0.0.1:8000"


export default {
    name:'Login',
      setup: () => ({ v$: useVuelidate() }),
   data(){
        return{
          formData:{
            password:'',
            faculty_number:'',
            device_name: 'browser',
         },
          errors:{}
        }
   },
   validations(){
     return {
       formData:{
       faculty_number:{required},
       password:{required},
       }
     }
   },
     methods : {
       
      
      login(){

          this.v$.$validate()

            if(!this.v$.$error){
      axios.get('/sanctum/csrf-cookie').then(response => {
        axios.post('/api/login', this.formData).then((response)=>{
           localStorage.setItem('isLoggedIn','true');
           localStorage.setItem('token',response.data);
         
          //   this.$router.push({name:'Dashboard'});
        this.$router.push('Dashboard', () => this.$router.go(0))

          }).catch((errors)=>{
       this.errors = errors.response.data.errors
          })

              }); //end of axios


            }else{
           console.log('there are rquired thing')
            }
        //this.v$.$touch();
   //console.log(this.v$)
     /*  
console.log('login'); */
      
      }
    } 
}
</script>


<style>



.text-line {
    background-color: transparent;
    color: #000000;
    outline: none;
    outline-style: none;
    border-top: none;
    border-left: none;
    border-right: none;
    border-bottom: solid black 1px;
    padding: 3px 10px;
}

.form-check-input {
  border: 1px solid #ff9807;
}

.form-label {
  font-family: Century Gothic;
  font-weight: 1000;
  color:black;

}
.loginbtn{
     border-radius:15px;
	border:solid #ff9807;
  background: #ff9807;
	display:inline-block;
	cursor:pointer;
	color: #545454;
	font-family:Century Gothic;
	font-size:17px;
	padding:16px 100px;
  font-weight: 1000;
	
}
.form-check-label{
  font-family: Century Gothic;
  font-size: 15px;
}




</style>
