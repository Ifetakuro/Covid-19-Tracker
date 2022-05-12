<template>
  <main v-if="!loading">
   <DataTitle :text="titleCountry" :dataDate="date" />
   <DataBoxes  :status="status" :country="country" @get-state="getState" :states='states'/>
   <!-- <StatesSelect :states='states' @get-state="getState"/> -->
  </main>
  <main v-else class="flex flex-col align-center justify-center text-center min-h-[70vh]">
    <div class="text-gray-500 text 3xl mt-10 font-medium">
      Fetching Data....
    </div>
    <img :src="loadingImage" class="w-24 m-auto" alt="Loading image">
  </main>
</template>

<script>
// @ is an alias to /src
import DataTitle from '@/components/DataTitle'
import DataBoxes from '@/components/DataBoxes'
// import StatesSelect from '@/components/StatesSelect'

export default {
  name: 'Home',
  components: {
    DataTitle,
    DataBoxes,
    // StatesSelect
  },
  data() {
    return {
      loading: true,
      titleCountry: 'Nigeria',
      date: new Date(),
      status: {},
      country: {},
      states: [],
      loadingImage: require('../assets/images/hourglass.gif')
    }
  },
  methods: {
    async fetchCovidData() {
      const response = await fetch('https://covidnigeria.herokuapp.com/api')
      const result = await response.json();
      return result
    },
    // emitted method from StatesSelect
    getState(state) {
      this.status = state
    }
  },
  async created() {
    const {data} = await this.fetchCovidData();
    this.country = data;
    this.status = data.states[0];
    this.states = data.states;
    this.loading = false
  }
}
</script>
