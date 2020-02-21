<template>
  <div class="signup">
    <div class="box">
      <span>Bienvenue</span>
      <input type="text" v-model="name" placeholder="Votre nom" />
      <input type="text" v-model="start" placeholder="Votre lieu de départ" />
      <input type="text" v-model="end" placeholder="Votre lieu de d'arrivé" />
      <button v-on:click="register">register</button>
    </div>
  </div>
</template>

<script>
import config from "@/config";
import Cookies from "js-cookie";

export default {
  /* eslint no-console: ["error", { allow: ["log", "error"] }] */
  name: "signup",

  data: () => ({
    name: 'Futaba',
    start: 'Brest',
    end: 'Rennes'
  }),

  methods: {
    register: async function() {
      const myInit = {
        method: "POST",
        headers: {
          "Access-Control-Allow-Origin": "*",
          "Content-Type": "application/json",
          Accept: "application/json"
        },
        body: JSON.stringify({
          name: this.name,
          home: this.start,
          work: this.end
        })
      };

      const { api } = config;

      try {
        const response = await fetch(api.baseUrl + "citizen", myInit);
        const data = await response.json();
        console.log(data[0].id);
        Cookies.set("token", data[0].id);
      } catch (err) {
        alert(
          "Désolé du désagrement nous avons un problème de CORS veuillez vous connecter avec un compte déjà existant"
        );
      }
    },
    suppr: async function() {
      const myInit = {
        method: "DELETE",
        headers: {
          "Access-Control-Allow-Origin": "*",
          "Access-Control-Allow-Methods": "POST, GET, PUT, OPTIONS, DELETE",
          "Access-Control-Allow-Headers":
            "Access-Control-Allow-Methods, Access-Control-Allow-Origin, Origin, Accept, Content-Type",
          "Content-Type": "application/json",
          Accept: "application/json"
        }
      };
      const { api } = config;
      await fetch(api.baseUrl + "citizen/24", myInit);
    }
  }
};
</script>

<style lang="css" scoped>
.signup {
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