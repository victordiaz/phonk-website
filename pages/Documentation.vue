<template>
  <div id = "container_documentation">
    <div class = "header">
      <h2>Documentation</h2>
      <div>The API reference is still work in progress, help! :)</div>
    </div>
    <documentation :documentation = "pdata"></documentation>
  </div>
</template>

<script>
import data from '~/static/static/documentation.json'
import Documentation from '~/components/Documentation.vue'

export default {
  components: {
    Documentation
  },
  async asyncData ({env, params}) {
    return { pdata: data }
    /*
    let { data } = await axios.get('http://127.0.0.1:3000/static/data.json')
    return { pdata: data }
    */
  }
}
</script>

<style lang = "less">
@import "../assets/variables.less";

#container_documentation {
  padding: 20px;

  .header {
    margin-bottom: 20px;
  }
}


</style>
