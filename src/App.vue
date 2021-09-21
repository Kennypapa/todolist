<template>
  <div>
    <mainform></mainform>
  </div>
</template>

<script>
import MainForm from './components/MainForm.vue'
export default {

  name: 'App',
  components: {
    'mainform' : MainForm
  }
}
</script>

<style>
body {
  background-color: #d3d3d382;
}
</style>
