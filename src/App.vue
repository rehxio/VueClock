<template>
  <html-clock theme="red-lcd"></html-clock>
</template>

<script>
  import ClockHTML from './components/ClockHTML';
  export default {
    components: {
      'html-clock': ClockHTML
    }
  }
</script>

<style>
  :root {
    text-align: center;
  }
  
  h1 {
    font-family: Montserrat, Impact, sans-serif;
    font-size: 72px;
  }
</style>
