<template>
  <footer class="bg-gray-800 w-full p-6 text-center text-zinc-300 text-xs font-medium">
    <p class="mb-2">Oluwafisayo Takuro &copy; {{getYear}}</p>
    <p>API from <span><a href="https://documenter.getpostman.com/view/9282328/SzYaUxJy" target="_blank" rel="noopener noreferrer">POSTMAN</a></span></p>
  </footer>
</template>

<script>
export default {
  name: 'Footer',
  computed: {
    getYear() {
      let date = new Date();
      let year = date.getFullYear();
      return year;
    }
  }
}
</script>

<style>

</style>