<template>
  <div id = "container">
    <download></download>
    <features></features>

    <!-- download area -->
    <div class = "download-area">
      <div class = "top-align">
        <h2>Download</h2>
        <p class = "current-version">Current version <span>1.0</span></p>
      </div>
      <p class = "notice">The following download links are the "official" ones.<br />Downloading Phonk from any other link will NOT guarantee the correct function of the app.</p>
      <ul class = "links">
        <li><a><img src = "/static/img/logo_f-droid.png" />F-droid Open Source App Store</a></li>
        <li><a><span>APK</span>APK File</a></li>
        <li><a><img src = "/static/img/logo_play-store.png" />Google Play Store</a></li>
      </ul>
      <!--
      <li><a>Download older APK</a></li>
      -->
      <ul>
      </ul>
    </div>

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

.download-area {
  background: @backgroundColor;
  color: white;
  border-radius: 3px;
  padding: 20px 15px;
  margin: 30px 0;

  .top-align {
    display: flex;
    margin-bottom: 15px;
  }

  h2 {
    font-weight: 800;
    flex: 2;
  }

  .notice {
    // border: 1px solid @textColorSecondary;
    background: #fff1;
    padding: 15px;
    border-radius: 3px;
    margin: 30px 10px;
  }

  .current-version {
    color: @accentColor;
  }

  .links {
    display: flex;
    flex-direction: column;
    margin: 50px 0;

    li {
      margin-bottom: 22px;
    }

    img, span {
      display: flex;
      align-items: center;
      justify-content: center;
      font-weight: 800;
      width: 52px;
      height: 52px;
      margin-right: 20px;
    }

    a {
      display: flex;
      align-items: center;
      background: @accentColor;
      border-radius: 3px;
      padding: 10px;
      cursor: pointer;
      box-shadow: 2px 2px 2px 2px #0005;

      &:hover {
        background: lighten(@accentColor, 10%);
      }

      &:active {
        background: darken(@accentColor, 5%);
      }
    }
  }
}

</style>
