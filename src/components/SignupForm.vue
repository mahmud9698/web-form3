<template>
    <form @submit.prevent="handleSubmit">
      <!-- v-model for 2 way data binding -->
      
      <label>Email</label>
      <input type="email" v v-model="email" required>
  
      <label>Password</label>
      <input :type="passwordFieldType" v-model="password" required>
      <div>
        <button class="btnShowHide" type="password" @click="showhidePassword">Show/Hide Password</button>
      </div>
      <div v-if="passwordError" class="error">{{ passwordError }}</div>
        
      <label>Role</label>
      <select v-model="role" required>
          <option value="Front End">Front End Developer</option>
          <option value="Back End">Back End Developer</option>
          <option value="Fullstack">Full Stack Developer</option>
      </select>
      
      <!-- Using keyboard event -->
      <label>Skills (use alt + "," to insert another skills)</label>
      <input type="text" v-model="tempSkill" @keyup.alt="addSkill">
      <div v-for="skill in skills" :key="skill" class="pill">
        <span @click="deleteSkill(skill)">{{ skill }}</span>
      </div>

      <div class="terms">
          <input type="checkbox" required v-model="term">
          <label>Accept term and condition</label>
      </div>
      
      <div class="submit">
        <button class="btnSubmit">Create an Account</button>
      </div>
    </form>
  
    <!-- <p>Email: {{ email }}</p>
    <p>Password: {{ password }}</p>
    <p>Role: {{ role }}</p>
    <p>Term: {{ term }}</p> -->
    
  </template>
  
  <script>
  export default {
      data() {
          return {
              email: '',
              password: '',
              passwordFieldType: "password",
              role: '',
              term: false,
              tempSkill: '',
              skills: [],
              passwordError: ''
          }
      },
      methods: {
        showhidePassword () {
            this.passwordFieldType = this.passwordFieldType === "password" ? "text" : "password"
        },
        addSkill(event) {
            if (event.key === ',' && this.tempSkill){
                //to check whether new skill enter is/are already in array 
                if (!this.skills.includes(this.tempSkill)){ 
                    this.skills.push(this.tempSkill)
                }
                this.tempSkill=''
            }
        },
        deleteSkill(skill){
            this.skills = this.skills.filter ((item) => {
                return skill !== item
            })
        },
        handleSubmit() {
            //validate password
            this.passwordError = this.password.length > 5 ? 
            '': 'Password must atleast 6 character'

            if (!this.passwordError) {
                console.log('Email: ', this.email)
                console.log('Password: ', this.password)
                console.log('Role: ', this.role)
                console.log('Skills: ', this.skills)
                console.log('Term: ', this.term)
            }
        }
      }
  }
  </script>
  
  <style>
  form {
      max-width: 420px;
      margin: 30px auto;
      background: white;
      text-align: left;
      padding: 40px;
      border-radius: 10px;
  }
  label{
      color: #aaa;
      display: inline-block;
      margin: 25px 0 15px;
      font-size: 0.6em;
      text-transform: uppercase;
      letter-spacing: 1px;
      font-weight: bold;
  }
  input, select{
      display: block;
      padding: 10px 6px;
      width: 100%;
      box-sizing: border-box;
      border: none;
      border-bottom: 1px solid #ddd;
      color: #555;
  }
  input[type="checkbox"]{
      display: inline-block;
      width: 16px;
      margin: 0 10px 0 0;
      position: relative;
      top: 2px;
  }
  .pill{
    display: inline-block;
    margin: 20px 10px 0 0;
    padding: 6px 12px;
    background: #eee;
    border-radius: 10px;
    font-size: 12px;
    letter-spacing: 1px;
    font-weight: bold;
    color:#777;
    cursor: pointer;
  }
  .btnSubmit{
    background: crimson;
    border: 0;
    padding: 10px 20px;
    margin-top: 20px;
    color: white;
    border-radius: 20px;
  }
  .btnShowHide {
    background: blueviolet;
    border: 0;
    padding: 10px 15px;
    margin-top: 10px;
    color: white;
    border-radius: 20px;
  }
  .submit{
    text-align: center;
  }
  .error{
    color: red;
    margin-top: 10px;
    font-size: 0.8em;
    font-weight: bold;
  }
  </style>