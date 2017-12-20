<template>
  <div id = "devices">
    <div id = "webbrowser" class = "device">
      <div><p class = "url">http://192.168.178.25:8585</p></div>
      <img src = "static/img/webide3.png" />
      <p id = "code">{{code}}</p>
    </div>
    <div id = "phone" class = "device" v-bind:class = "{ qq: showVideo}" >
      <div class = "img_container">
        <video ref = "phoneApp" id = "app" poster = "static/app1.jpg" muted>
          <source src="static/app1.mp4" type="video/mp4">
          <source src="static/app1.webm" type="video/webm">
          I'm sorry; your browser doesn't support HTML5 video in WebM with VP8/VP9 or MP4 with H.264.
        </video>
        <!-- <img id = "app" src = "./img/phone2.jpg" /> -->
        <img id = "so" src = "static/img/phone2.jpg" />
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'

export default {
  data () {
    return {
      code: 'qq',
      showVideo: false
    }
  },
  mounted () {
    axios
      .get('static/main.txt')
      .then(response => {
        this.writeCode(response.data)
      }).catch(e => {
        console.log(e)
      })

    this.$refs.phoneApp.play()
  },
  methods: {
    // load text code
    writeCode: function (data) {
      var index = -1
      var writingInterval = setInterval(() => {
        this.code = data.substring(0, index++)

        if (index > data.length) {
          clearInterval(writingInterval)
          // $('#phone #app').attr("src", "./img/phone.png")

          this.$refs.phoneApp.controls = false
          this.$refs.phoneApp.play()

          this.$refs.phoneApp.onplay = (e) => {
            setTimeout(() => {
              this.showVideo = false
            }, 7000)
          }

          setTimeout(() => {
            this.showVideo = true
          }, 1000)
        }
      }, 12)
    }
  }

}
</script>

<style>

</style>
