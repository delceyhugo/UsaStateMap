<script setup>
import { ref } from 'vue'
import Map from './components/Map.vue'
import Theheader from './components/Theheader.vue'
import StateList from './components/StateList.vue'
const stateList = ref(null)
const mapEl = ref(null)
const mapInterraction = ref(true)

</script>

<template>
  <main>
    <section id="Map-content">
      <Map ref="mapEl" :interactive="mapInterraction" @onHover="(e) => stateList.handleOnHover(e)" @onLeave="(e) => stateList.handleOnLeave(e)" />
    </section>
  </main>
</template>

<style lang="scss" scoped>
  main{
    height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    section{
      display: flex;
      justify-content: center;
      align-items: center;
      width: 90%;
      height: 90%;
      border-radius: 25px;
      box-shadow: 0px 0px 10px 0px #00000080;
      background-color: #1a1816;
    }
  }
</style>
