<template>
  <form @submit.prevent="register">
      <label>Email:</label>
      <input type="email" required v-model="email">

      <label>Password:</label>
      <input type="password" required v-model="password">

      <label>Role:</label>
      <select v-model="role">
          <option value="fullStack">FullStack Developer</option>
          <option value="frontend">Frontend Developer</option>
          <option value="backend">Backend Developer</option>
         
      </select>

    <label>Skills:</label>
    <input type="text" v-model="tempSkill" @keyup="addSkill">

    <div v-for="skill in skills" :key='skill' class="pill">
        <span @click="deleteSkill(skill)">{{ skill }}</span>
    </div>
        
    <div class="terms">
        <input type="checkbox" v-model="terms">
        <label>Accept Terms and conditons</label>

    </div>
    <div class="submit">
        <button>Register</button>
    </div>

  </form>

  <p>Email: {{ email }}</p>
  <p>Password: {{ password }}</p>
  <p>Role: {{ role }}</p>
  <p>Terms: {{ terms }}</p>
  
</template>

<script>
export default {
data() {
    return {
        email: 'sador',
        password: '',
        role: '',
        terms: 'false',
        tempSkill: '',
        skills: [],
        passwordError: ''
    }
},
methods: {
    addSkill(e) {
        if(e.key === ',' && this.tempSkill){
            if (!this.skills.includes(this.tempSkill)){
            this.skills.push(this.tempSkill.substring(0, this.tempSkill.length-1))
            }
            this.tempSkill = ''

        }
    },
    deleteSkill(skill) {
      this.skills = this.skills.filter((item) => {
          return item !== skill
      })  
    },
    register() {
        // do validation and
        // save to the database
    }
}
}
</script>

<style>
form {
  max-width: 500px;
  margin: 20px auto;
  background: white;
  text-align: left;
  padding: 30px;
  border-radius: 10px;
}
label {
  color: rgb(106, 101, 101);
  display: inline-block;
  margin: 25px 0px 15px;
  font-size: 1.1rem;
  text-transform: uppercase;
  font-weight: bold;
}
input, select {
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

.pill {
    display: inline-block;
    background: #555;
    border-radius: 5px;
    color: white;
    margin: 10px 10px 10px 0;
    padding: 5px  10px;
    cursor: pointer;
}

button {
    background: #555;
    color: white;
    border-radius: 10px;
    padding: 10px 20px;
    border: 0;
    font-size: 1.2rem;
    margin: 10px;
}

button:hover {
    background: rgb(42, 40, 40);
}

.submit {
    text-align: center;
}


</style>