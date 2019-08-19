<template>
  <div id="app">
   <Application />
  </div>
</template>

<script>
import Application from './Application'
  export default {
    name: 'app',
    components:{
      Application,
    }
  }
</script>


<!-- Global CSS -->
<style>
  code {
    font-family: Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, serif;
    font-size: 0.9em;
    white-space: pre-wrap;
    color: #2c3e50;
  }

  code::before, code::after {
    content: '`';
  }
</style>

<!-- Scoped component css -->
<style scoped>
  #app {
    text-align: center;
  }


  .bottom {
    padding: 80px 10px;
    font-size: 24px;
    font-weight: 300;
  }

  .fade {
    font-size: 14px;
  }

</style>
