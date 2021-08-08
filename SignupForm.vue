<template>

<div>
<form >
    <h3 align="center">REGISTRATION FORM</h3>
    <label>First Name:</label>
    <v-text-field type="firstName" required v-model="firstName"></v-text-field>

    <label>last Name:</label>
    <v-text-field type="lastName" required v-model="lastName"></v-text-field>

    <label>Email:</label>
    <v-text-field type="email" required v-model="email"></v-text-field>

    <label>Password:</label>
    <v-text-field type="password" required v-model="password"></v-text-field>

    <label>Role:</label>
    <select v-model="role">
      <option value="developer">Web Developer</option>
      <option value="designer">Web Designer</option>
    </select>

<div class="terms">
   <input type="checkbox" v-model="terms" required>
   <label>Accept terms and conditions</label>
</div>

<div class="submit">
   <v-btn color="primary" elevation="2" @click="handleSubmit" >Create an Account</v-btn>
</div>

  <v-alert v-show="isalert" type="success">Registered Successfully</v-alert>
</form>
</div>
    
</template>

<script>
import Vue from "vue"
import VueSimpleAlert from "vue-simple-alert"
Vue.use(VueSimpleAlert)
let array = []
let obj ={}

export default {
    
    components: {

  },
data() {

  return {

   firstName: '',
   lastName: '',
   email: '',
   password: '',
   role: 'designer',
   terms: false,
   isalert: false
   
  }

},
methods: {

    handleSubmit() {
        if(this.firstName && this.lastName && this.email && this.password){
        //this.isalert = true
              obj ={
                 FirstName : this.firstName,
                 LastName : this.lastName,
                 Email : this.email,
                 Password : this.password,
                 Role : this.role
             }
             array.push(obj)
             console.log(array)
             localStorage.setItem("Email", JSON.stringify(array))
             this.firstName = ''
             this.lastName = ''
             this.email = ''
             this.password = ''
             this.terms = false
             this.$fire({
                 title: "Registered Successfully..!",
                 type: "success",
                 timer: 1000
             })
        }else {
            this.$fire({
                title: "Registration Failed",
                text: "Fill all fields",
                type: "error",
                timer: 2000
            })
        }

    }
}


}

</script>


<style>
form {
    max-width: 520px;
    margin: 30px auto;
    background: rgb(136, 231, 200);
    text-align: left;
    padding: 40px;
    border-radius: 10px;
}
label {
    color: rgb(236, 18, 18);
    display: inline-block;
    margin: 25px 0 15px;
    font-size: 0.8em;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-weight: bold;
}
input,select {
    display: block;
    padding: 10px 6px;
    background: #faf9f9;
    border-radius: 10px;
    width: 100%;
    box-sizing: border-box;
    border: none;
    border-bottom: 1px solid #ddd;
    color: #555;
}
input[type="checkbox"] {
    display: inline-block;
    width: 16px;
    margin: 0 10px 0 0;
    position: relative;
    top: 2px;
}
.pill {
    display: inline-block;
    margin: 20px 10px 0 0;
    padding: 6px 12px;
    background:#eee;
    border-radius: 20px;
    font-size: 12px;
    letter-spacing: 1px;
    font-weight: bold;
    color:#777;
    cursor: pointer;
}
button {
    background: #1960ee;
    border: 0;
    padding: 10px 20px;
    margin-top: 20px;
    color: rgb(235, 29, 29);
    border-radius: 20px;
}
.submit {
    text-align: center;
}

</style>