<script>
import axios from "axios";
export default {
  name: "App",
  data() {
    return {
      EmailEl: "",
      emailList: [],
    };
  },
  mounted() {
    for (let i = 0; i < 10; i++) {
      axios
        .get("https://flynn.boolean.careers/exercises/api/random/mail")
        .then((email) => {
          this.EmailEl = email.data.response;
          this.emailList.push(this.EmailEl);
        });
    }
  },
};
</script>
<template>
  <div class="container">
    <h1>Lasciati ispirare da queste email!</h1>
    <ul class="container" v-if="emailList.length == 10">
      <li v-for="(email, index) in emailList">
        <strong>Opzione {{ index + 1 }} : </strong> {{ email }}
      </li>
    </ul>
  </div>
</template>
<style scoped>
h1 {
  margin-top: 1rem;
}
ul {
  list-style: none;
  padding: 3rem;

  li {
    margin-top: 1rem;
    margin-left: 1rem;
    padding: 1rem;
    background-color: violet;
    border-radius: 1rem;
  }
}

li:hover {
  filter: drop-shadow(0 0 15px #9c569e);
  scale: 1.01;
}
</style>
