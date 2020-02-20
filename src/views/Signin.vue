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
export default {
  name: "signin",

  async created() {
    

    var myInit = {
      method: "GET",
    };
    /* eslint no-console: ["error", { allow: ["log", "error"] }] */
    const response = await fetch("http://localhost:8080/citizen/list", myInit);
    const data = await response.json();
    console.log(data)
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