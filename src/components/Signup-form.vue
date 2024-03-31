<template>
  <form @submit.prevent="handleSubmit">
    <label for="">Email:</label>
    <input type="email" required v-model="email" />

    <label for="">Password:</label>
    <input type="password" required v-model="password" />
    <div style="color: red">{{ passwordError }}</div>
   
    <label for="">roll:</label>
    <select v-model="roll" name="" id="">
      <option value="front-end">FrontEnd</option>
      <option value="back-end">BackEnd</option>
    </select>

    <label>Skills</label>
    <input type="text" v-model="tempSkill" @keyup.ctrl="enterValue" />

    <ul>
      <li
        @click="deleteSkill"
        v-for="skill in skills"
        :key="skill"
        class="pill"
      >
        {{ skill }}
      </li>
    </ul>

    <div class="terms">
      <input type="checkbox" required v-model="term" />
      <label>Accept Terms & Conditions</label>
    </div>
    <div class="submit">
      <button>Create an account</button>
    </div>
  </form>
</template>

<script>
export default {
  data() {
    return {
      term: false,
      roll: "",
      email: "",
      password: "",
      tempSkill: "",
      skills: [],
      passwordError: '',
    };
  },
  methods: {
    enterValue(e) {
      if (e.key === "," && this.tempSkill) {
        if (!this.skills.includes(this.tempSkill)) {
          this.skills.push(this.tempSkill);
        } else {
          alert("Skill already exists");
        }
        this.tempSkill = "";
      }
    },
    deleteSkill(index) {
      this.skills.splice(index, 1);
    },
    handleSubmit() {
     //validate password
      this.passwordError = this.password.length < 6 ? 'Password must be at least 6 characters' : '';
    },
  },
};
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
label {
  color: #aaa;
  display: inline-block;
  margin: 25px 0 15px;
  font-size: 0.8em;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}
input {
  display: block;
  width: 100%;
  padding: 10px 6px;
  border: none;
  border-bottom: 1px solid #ddd;
  color: 555;
  box-sizing: border-box;
}
select {
  display: block;
  width: 100%;
  padding: 10px 6px;
  border: #9c9c9c 1px solid;
  border-radius: 20px;
  color: 555;
  box-sizing: border-box;
}
input[type="checkbox"] {
  display: inline-block;
  width: 16px;
  margin: 0 10px 0 0;
  position: relative;
  top: 2px;
}
ul {
  list-style: none;
}
.pill {
  display: inline-block;
  padding: 5px 10px;
  background: #f1f1f1;
  border-radius: 20px;
  margin: 5px;
  cursor: pointer;
  font-weight: bold;
}
button {
  background: #4c6cb4;
  color: white;
  border: none;
  padding: 10px 20px;
  border-radius: 20px;
  cursor: pointer;

  margin-top: 20px;
}
.submit {
  text-align: center;
}
</style>
