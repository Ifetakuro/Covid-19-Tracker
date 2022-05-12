<template>
  <div class="text-gray-800">
    <!-- COUNTRY SECTION -->
    <div class="grid md:grid-cols-2 gap-6">
      <!-- box 1 -->
      <div class="shadow-md p-8 text-center rounded box hover:border-[#07BEB8] border">
        <h3 class="text-2xl font-bold mb-4">Cases</h3>
        <div class=" text-xl mb-4">
          <span class="font-bold">Confirmed cases:</span>
          {{ numbersWithCommas(country.totalConfirmedCases)}}
        </div>
        <div class=" text-xl mb-4">
          <span class="font-bold">Active cases:</span>
          {{ numbersWithCommas(country.totalActiveCases)}}
        </div>
        <div class="text-xl mb-4">
          <span class="font-bold">Total tested: </span>
          {{ numbersWithCommas(country.totalSamplesTested)}}
        </div>
      </div>
      <!-- box 2 -->
      <div class="shadow-md p-8 text-center rounded box2 hover:border-[#07BEB8] border">
        <h3 class="text-2xl font-bold mb-4">Results</h3>
        <div class="text-xl mb-4">
          <span class="font-bold">Discharged:</span>
          {{ numbersWithCommas(country.discharged)}}
        </div>
        <div class="text-xl mb-4">
          <span class="font-bold">Death:</span>
          {{ numbersWithCommas(country.death)}}
        </div>
      </div>
    </div>

    <!-- STATE SECTION -->
    <div v-show='show'>
      <div class="text-center mt-12 mb-8" >
        <div class="flex md:flex-row flex-col align-center justify-center text-center md:gap-3 gap-2">
          <h2 class="md:text-3xl text-2xl font-bold">{{status.state}} state, Nigeria</h2>
          <StatesSelect :states='states' @get-state="getState"/>
        </div>
      </div>
      <div class="grid md:grid-cols-2 gap-6" v-if="status.state ">
        <!-- box 1 -->
        <div class="shadow-md p-8 text-center rounded box hover:border-[#07BEB8] border">
          <h3 class="text-2xl font-bold mb-4">Cases</h3>
          <div class=" text-xl mb-4">
            <span class="font-bold">Confirmed cases:</span>
            {{ numbersWithCommas(status.confirmedCases)}}
          </div>
          <div class=" text-xl mb-4">
            <span class="font-bold">Active cases:</span>
            {{ numbersWithCommas(status.casesOnAdmission)}}
          </div>
        </div>
        <!-- box 2 -->
        <div class="shadow-md p-8 text-center rounded box2 hover:border-[#07BEB8] border">
          <h3 class="text-2xl font-bold mb-4">Results</h3>
          <div class="text-xl mb-4">
            <span class="font-bold">Discharged:</span>
            {{ numbersWithCommas(status.discharged)}}
          </div>
          <div class="text-xl mb-4">
            <span class="font-bold">Death:</span>
            {{ numbersWithCommas(status.death)}}
          </div>
        </div>
      </div>
    </div>
    <!-- TOGGLE BUTTON -->
    <div class="text-center">
      <button class="bg-green-600 p-3 m-10 rounded shadow font-medium text-white hover:bg-green-900 cursor-pointer" @click='toggleState'>{{ show ? 'Hide State' : 'Show State'}}</button>
    </div>
  </div>
</template>

<script>
import StatesSelect from '@/components/StatesSelect'

export default {
  name: 'DataBoxes',
  components: {
    StatesSelect
  },
  data() {
    return {
      show: false,
    }
  },  
  props: ['status', 'country', 'states', 'get-state'],
  methods: {
    numbersWithCommas(x) {
      return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ',')
    },
    toggleState() {
      this.show = !this.show
      console.log(this.show)
    }
  }
}
</script>

<style scoped>
  .box {
    background: #68d8d664;
  }

  .box2 {
    background: #06999464;
  }

  h3 {
    color: #046a66;
  }

</style>