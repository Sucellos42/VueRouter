
<script setup>
import {useRoute, useRouter, RouterView} from "vue-router"
import cars from "../data/cars.json"
import ContactView from "@/views/ContactView.vue";

const route = useRoute()
const router = useRouter()

console.log(router)

const carId = parseInt(route.params.id)
const car = cars.find(c => c.id === parseInt(route.params.id))

const showContact = () => {
  if (carId === 4) return;
  return router.push(`/cars/${carId}/contact`)
}

</script>

<template>
  <div v-if="car">
    <h1>Carview</h1>
    <p>{{car.name}}</p>
    <p>{{car.price}}$</p>
    <p>{{car.year}}</p>
    <button @click="showContact">Click me for contact</button>
    <RouterView />
  </div>
  <div v-else>
    <h1>Car not found</h1>
  </div>
</template>

<style scoped>

</style>