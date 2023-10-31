<template>
    <form>
      <!-- v-model for 2 way data binding -->
      <label>Email</label>
      <input type="email" v v-model="email" required>
  
      <label>Password</label>
      <input type="password" v-model="password" required>
  
      <label>Role</label>
      <select v-model="role">
          <option value="Front End">Front End Developer</option>
          <option value="Back End">Back End Developer</option>
          <option value="Fullstack">Full Stack Developer</option>
      </select>
  
      <div class="terms">
          <input type="checkbox" required v-model="term">
          <label>Accept term and condition</label>
      </div>
  
    </form>
  
    <p>Email: {{ email }}</p>
    <p>Password: {{ password }}</p>
    <p>Role: {{ role }}</p>
    <p>Term: {{ term }}</p>
  </template>
  
  <script>
  export default {
      data() {
          return {
              email: '',
              password: '',
              role: '',
              term: false
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
  </style>