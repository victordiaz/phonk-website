<template>
  <div id = "container">
    <div id = "download">
      <a href = "#download-area">Download</a>
      <!-- <a href = "">Google Play</a> -->
      <a href = "https://github.com/victordiaz/phonk">Github</a>
    </div>

    <features></features>
    <download></download>

    <!-- commits
    <div>
      <h2>Activity</h2>
    </div>
    -->

  </div>
</template>

<script>
import Download from '~/components/Download.vue'
import Features from '~/components/Features.vue'

export default {
  components: {
    Download,
    Features
  }
}
</script>

<style lang = "less">
@import (reference) "../assets/variables.less";

#download {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
}

</style>
