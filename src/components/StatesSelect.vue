<template>
  <select @change="onChange" 
  v-model='selected' 
  class="form-select block border w-30 rounded border-[#06a49e] text-xs p-1 font-medium cursor-pointer">
    <option value="0" >Select a state in Nigeria</option>
    <option v-for="(state, index) in states" :value="state._id" :key="index" class="bg-[#68d8d664]" >{{state.state}}</option>
  </select>
</template>

<script>
export default {
  name: 'StatesSelect',
  props: ['states'],
  data() {
    return {
      selected: 0
    }
  },
  methods: {
    onChange() {
      const state = this.states.find((item) => item._id === this.selected)
      // emit to the grand parent
      this.$parent.$emit('get-state', state)
    }
  }
}
</script>

<style>

</style>