<template>
  <div class="navbar">
    <ul class="left-content">
      <li>
        <router-link class="home" tag="li" to="/home" v-if="isLoggedIn">
          <img src="@/assets/logobrb.png"/>
        </router-link>
      </li>
    </ul>
    <ul class="right-content">
      <li v-if="!isLoggedIn">
        <router-link to="/">
          <button>Se connecter</button>
        </router-link>
      </li>
      <li v-if="!isLoggedIn">
        <router-link to="/signup">
          <button>S'enregistrer</button>
        </router-link>
      </li>
      <li v-if="isLoggedIn">
        <router-link to="/userprofile">
        <button>Profile</button>
        </router-link>
      </li>
      <li v-if="isLoggedIn">
        <button v-on:click="disconnect">Se déconnecter</button>
      </li>
    </ul>
  </div>
</template>

<script>
import Cookies from "js-cookie";
export default {
  /* eslint no-console: ["error", { allow: ["log", "error"] }] */
  name: "navbar",

  data: () => ({
    isLoggedIn: false
  }),

  created() {
    const myCookie = !(Cookies.get("token") == null);
    this.isLoggedIn = myCookie;
    console.log(this.isLoggedIn);
  },

  methods: {
    disconnect: function() {
      Cookies.remove("token");
      window.location.replace("/");
    }
  }
};
</script>

<style lang="css" scoped>
.navbar {
  box-shadow: 0 0 3px rgba(0, 0, 0, 0.25);
  transition: background-color 0.3s ease-in-out;
  height: 5%;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
}
.left-content {
  display: flex;
  justify-content: left;
  align-items: center;
  height: 100%;
}
.right-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 100%;
  margin: 0 2%;
}
li {
  list-style: none;
  text-decoration: none;
}

li a {
    text-decoration: none;
}

img {
  height: 30%;
  width: 20%;
}

</style>