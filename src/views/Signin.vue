<template>
  <div class="signin">
    <div class="box">
      <span>Bienvenue</span>
      <input type="text" placeholder="votre nom" />
      <router-link to="/home">
        <button class="connexion">connexion</button>
      </router-link>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  name: "signin",

  async created() {
    /*var myHeaders = new Headers();
    myHeaders.append('Access-Control-Allow-Origin', '*')
    myHeaders.append('Access-Control-Allow-Methods', 'POST, GET, PUT, OPTIONS, DELETE')
    myHeaders.append('Access-Control-Allow-Headers', 'Access-Control-Allow-Methods, Access-Control-Allow-Origin, Origin, Accept, Content-Type')
    myHeaders.append('Content-Type', 'application/json')
    myHeaders.append('Accept', 'application/json')

    var myInit = {
      method: "GET",
      headers: myHeaders,
      mode: "cors",
      cache: "default"
    };*/
    /* eslint no-console: ["error", { allow: ["log", "error"] }] */
    const response = await axios("http://localhost:8080/citizen", { crossdomain: true });
    console.log(response)
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
</style>