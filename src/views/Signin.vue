<template>
  <div class="signin">
    <div class="box">
      <span>Bienvenue sur BrB</span>
      <input type="text" placeholder="votre nom (exemple Olivier)" v-model="username" />
      <button class="connexion" v-on:click="login">connexion</button>
    </div>
  </div>
</template>

<script>
import config from "@/config";
import Cookies from'js-cookie'
export default {
  /* eslint no-console: ["error", { allow: ["log", "error"] }] */
  name: "signin",

  data: () => ({
    username: ''
  }),

  methods: {
    login: async function() {
      const myInit = {
        method: 'GET'
      };

      const { api } = config;

      const response = await fetch(`${api.baseUrl}citizen`, myInit);
      const data = await response.json();

      let user = false;
      let tokenID;
      let i = 0
      for(i=0; i<data.length; i++){
        if (data[i].name == this.username){
          user = true
          tokenID = data[i].id
        }        
      }

      if (user) {
        Cookies.set("token", tokenID);
        alert("Vous êtes connecté");
        window.location.replace("/home");
      }
      else {
        alert("Le nom est incorrecte");
      }
    }
  }
};
</script>

<style lang="css" scoped>
.signin {
  height: 90%;
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
}
.box {
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.25);
  transition: background-color 0.3s ease-in-out;
  height: 30%;
  width: 30%;
  border-radius: 5px;
  display: flex;
  flex-direction: column;
  align-content: center;
  justify-content: space-evenly;
}

input {
  background-color: #fff;
  border: 1px solid #dfe0e6;
  color: #1c1c1f;
  font-size: 0.9375em;
  line-height: normal;
  margin: 0 auto;
}

button {
  margin: 0 auto;
}
</style>