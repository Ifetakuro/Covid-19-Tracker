<template>
  <div class="text-center mt-8">
    <div class="flex align-center justify-center text-center gap-3">
      <h2 class="text-3xl font-bold">{{text}}</h2>
      <img src="../assets/images/nigeria.png" alt="Nigeria flag" class="w-6 h-6 mt-2">
    </div>
    <div class="text-2xl mt-4 mb-10">
      {{timestamp}}
    </div>
  </div>
</template>

<script>
import moment from 'moment'
export default {
  name: 'DataTitle',
  props: ['text', 'dataDate' ],
  // install moment to format your date
  computed: {
    timestamp: function() {
      return moment(this.dataDate).format('MMMM Do YYYY, h:mm:ss a')
    }
  }
}
</script>

