<template>
  <form @submit.prevent="hundleSubmit">
    <label>email:</label>
    <input type="email" required v-model="email" />
    <label>password:</label>
    <input type="password" v-model="password" required autocomplete="on" />
    <div v-if="passwordError" class="pass">{{ passwordError }}</div>

    <select v-model="role">
      <option value="developer">web designer</option>
      <option value="designer">web developer</option>
    </select>
    <label>skils</label>
    <input type="text" v-model="tempSkill" @keyup.alt="addSkill" />
    <div v-for="skill in skills" :key="skill" class="pill">
      <p @click="deleteItem(skill)">{{ skill }}</p>
    </div>
    <div class="terms">
      <input type="checkbox" v-model="terms" required />
      <label>accept terms and conditions</label>
    </div>
    <div class="submit">
      <button>create an account</button>
    </div>
  </form>
  <p>email: {{ email }}</p>
  <p>password: {{ password }}</p>
  <p>role: {{ role }}</p>
  <p>terms accepted: {{ terms }}</p>
</template>

<script>
export default {
  data() {
    return {
      email: "",
      password: "",
      role: "",
      terms: false,
      tempSkill: "",
      skills: [],
      passwordError: "",
    };
  },
  methods: {
    addSkill(e) {
      if (e.key === "," && this.tempSkill) {
        if (!this.skills.includes(this.tempSkill)) {
          this.skills.push(this.tempSkill);
        }

        this.tempSkill = "";
      }
    },
    deleteItem(skill) {
      this.skills = this.skills.filter((item) => {
        return skill !== item;
      });
    },
    hundleSubmit() {
      this.passwordError =
        this.passwordError.length > 5 ? "" : "password be atleast 6 character";
      if (!this.passwordError) {
        console.log("email", this.email);
        console.log("password", this.password);
        console.log("rol", this.role);
        console.log("skill", this.skills);
        console.log("terms accepted", this.terms);
      }
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
  font-size: 0.6em;
  text-transform: uppercase;
  letter-spacing: 1px;
  font-weight: bold;
}
input,
select {
  display: block;
  padding: 10px 6px;
  width: 100%;
  box-sizing: 100%;
  border: none;
  border-bottom: 1px solid #ddd;
  color: #555;
}
input[type="checkbox"] {
  display: inline-block;
  width: 10px;
  margin: 0 10px 0 0;
  position: relative;
  top: 2px;
}
.pill {
  display: inline-block;
  margin: 20px 10px 0 0;
  padding: 6px 12px;
  background: #eee;
  border-radius: 20px;
  font-size: 12px;
  letter-spacing: 1px;
  font-weight: bold;
  color: #7777;
}
button {
  background: #0b6dff;
  border: 0;
  padding: 10px 20px;
  margin-top: 20px;
  color: white;
  border-radius: 20px;
}
.submit {
  text-align: center;
}
.pass {
  color: red;
}
</style>