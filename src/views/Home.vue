<template>
  <div class="home">
    <h1>Bonjour {{username}}</h1>
    <h2>Le trajet le plus court entre {{startAddress}} et {{endAddress}} est {{trajet}}</h2>
  </div>
</template>

<script>
import config from "@/config";
import Cookies from "js-cookie";
export default {
  /* eslint no-console: ["error", { allow: ["log", "error"] }] */
  name: 'home',

  data: () => ({
    username: '',
    trajet: '',
    start: '',
    end: '',
    endAddress: '',
    startAddress: ''
  }),

  async created() {/* eslint no-console: ["error", { allow: ["log", "error"] }] */
    const myInit = {
      method: "GET"
    };

    const { api, gMap } = config
    const userID = Cookies.get("token")
    const response = await fetch(`${api.baseUrl}citizen/${userID}`, myInit)
    const data = await response.json()
    
    this.username = data.name
    this.start = data.home
    this.end = data.work
    const PROXY_URL = 'https://cors-anywhere.herokuapp.com/';

    const apiDriving = `https://maps.googleapis.com/maps/api/directions/json?origin=${this.start}&destination=${this.end}&key=${gMap.apiKey}`
    const apiWalking = `https://maps.googleapis.com/maps/api/directions/json?origin=${this.start}&destination=${this.end}&mode=walking&key=${gMap.apiKey}`
    const apiBicycling = `https://maps.googleapis.com/maps/api/directions/json?origin=${this.start}&destination=${this.end}&mode=bicycling&key=${gMap.apiKey}`
    const responseGD = await fetch(PROXY_URL+apiDriving, myInit)
    const dataGD = await responseGD.json()
    const responseGW = await fetch(PROXY_URL+apiWalking, myInit)
    const dataGW = await responseGW.json()
    const responseGB = await fetch(PROXY_URL+apiBicycling, myInit)
    const dataGB = await responseGB.json()
    this.startAddress= dataGD.routes[0].legs[0].start_address
    this.endAddress= dataGD.routes[0].legs[0].end_address
    const drivingValue = dataGD.routes[0].legs[0].duration.value
    const walkingValue = dataGW.routes[0].legs[0].duration.value
    const bicyclingValue = dataGB.routes[0].legs[0].duration.value
    if((drivingValue <= walkingValue) && (drivingValue <= bicyclingValue)){
      this.trajet = `en voiture et dure ${dataGD.routes[0].legs[0].duration.text}`
    } else if ((bicyclingValue <= drivingValue) && (bicyclingValue <= walkingValue)){
      this.trajet = `en vélo et dure ${dataGD.routes[0].legs[0].duration.text}`
    } else {
      `à pied et dure ${dataGD.routes[0].legs[0].duration.text}`
    }
  }
};
</script>

<style scoped>
.home {
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  height: 100%;
  width: 100%;
}
</style>
