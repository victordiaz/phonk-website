<template>
  <div id = "container">
    <download></download>
    <features></features>

    <!-- download area -->
    <div>
      <h2>Download</h2>
    </div>

    <!-- commits -->
    <div>
      <h2>Activity</h2>
    </div>

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

<style>

</style>
