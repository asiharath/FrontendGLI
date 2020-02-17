<template>
  <div class="signup">
    <div class="box">
      <span>Bienvenue</span>
      <input type="text" v-model="name" placeholder="Votre nom" />
      <input type="text" v-model="start" placeholder="Votre lieu de départ" />
      <input type="text" v-model="end" placeholder="Votre lieu de d'arrivé" />
      <button>register</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "signup",
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