<template>
  <article class="relative p-8 w-full max-w-2xl mx-auto mb-14">
    <h2 class="text-center text-white text-2xl font-[500] lg:text-3xl">IP Address Tracker</h2>

    <form @submit.prevent="getIpInfo" class="flex justify-center mt-4 lg:mt-8">
      <input v-model="queryIp" type="text" placeholder="Enter your IP Address"
        class="py-2 lg:py-4 px-4 rounded-l-lg outline-none w-full">
      <button type="submit" class="bg-black px-4 lg:px-6 hover:opacity-50 transition-all duration-300"><img
          src="images/icon-arrow.svg" alt=""></button>
    </form>
  </article>

  <DashInfo v-if="ipInfo" :ipInfo="ipInfo" />

  <div id="map" class="h-screen z-10">

  </div>
</template>

<script setup>
import leaflet from 'leaflet'
import DashInfo from '@/components/DashInfo.vue';
import { ref, onMounted } from 'vue'
import axios from 'axios'

const queryIp = ref("")
const ipInfo = ref(null)


let map
onMounted(() => {
  map = leaflet.map('map').setView([51.505, -0.09], 13);

  leaflet.tileLayer('https://tile.openstreetmap.org/{z}/{x}/{y}.png', {
    maxZoom: 19,
    attribution: '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>'
  }).addTo(map);

  leaflet.marker([51.505, -0.09]).addTo(map);
})

const getIpInfo = async () => {
  try {
    const data = await axios.get(`https://geo.ipify.org/api/v2/country,city?apiKey=at_tAW2nW0pxM7lHDAcNudsq1Zpq7UvU&ipAddress=${queryIp.value}`)
    const result = data.data
    ipInfo.value = {
      address: result.ip,
      location: result.location.region,
      timezone: result.location.timezone,
      isp: result.isp,
      lat: result.location.lat,
      lng: result.location.lng
    }
    leaflet.marker([ipInfo.value.lat, ipInfo.value.lng]).addTo(map);
    map.setView([ipInfo.value.lat, ipInfo.value.lng])
  } catch (err) {
    alert(err.message)
  }
}
</script>

