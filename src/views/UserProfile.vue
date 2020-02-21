<template>
  <div class="userprofile">
    <div class="box">
      <span>Edit</span>
      <input v-model="name" v-bind:placeholder="name" />
      <input v-model="start" v-bind:placeholder="start" />
      <input v-model="end" v-bind:placeholder="end" />
      <button>save</button>
    </div>
  </div>
</template>

<script>
import config from "@/config";
import Cookies from "js-cookie";
export default {
  name: "userprofile",
  
  data: () => ({
    name: '', 
    start: '', 
    end: ''
  }),

  async created() {
    const myInit = {
        method: 'GET'
      };

      const { api } = config;
      const userID = Cookies.get('token');
      const response = await fetch(`${api.baseUrl}citizen/${userID}`, myInit);
      const data = await response.json();
      this.name = data.name
      this.start = data.home
      this.end = data.work
  }
};
</script>

<style lang="css" scoped>
.userprofile {
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