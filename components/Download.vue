<template>
  <!-- download area -->
  <div id = "download-area">
    <div class = "top-align">
      <h2>Download</h2>
      <p class = "current-version">Current version <span>1.0</span></p>
    </div>
    <p class = "notice">The following download links are the "official" ones.<br />Downloading Phonk from any other link will NOT guarantee the correct function of the app.</p>
    <ul class = "links">
      <li><a href = "https://github.com/victordiaz/phonk/releases" download><div class = "download_type apk">APK</div><p>APK File</p></a></li>
      <!-- <h1>Soon F-droid and Google Play Store downloads will be enabled</h1> -->
      <li class = "disabled"><a><img class = "download_type" src = "/static/img/logo_f-droid.png" /><p>F-droid Open Source App Store</p></a></li>
      <li class = "disabled"><a><img class = "download_type" src = "/static/img/logo_play-store.png" /><p>Google Play Store</p></a></li>
    </ul>
    <!--
    <li><a>Download older APK</a></li>
    -->
    <ul>
    </ul>
  </div>
</template>

<style lang = "less">
@import (reference) "../assets/variables.less";

#download-area {
  background: @backgroundColor;
  color: white;
  border-radius: 3px;
  padding: 25px;
  margin: 80px 0;

  .disabled {
    opacity: 0.2;
    cursor: not-allowed;
    pointer-events: none;
  }

  .top-align {
    display: flex;
    margin-bottom: 15px;
  }

  h2 {
    font-weight: 800;
    flex: 2;
    color: @accentColor;
  }

  .notice {
    // border: 1px solid @textColorSecondary;
    // background: #fff1;
    // padding: 15px;
    border-radius: 3px;
    // margin: 30px 10px;
  }

  .current-version {
    color: @accentColor;
  }

  .links {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
    margin: 50px 0 0 0;
    text-align: center;

    h1 {
      margin-bottom: 20px;
    }

    li {
      margin-bottom: 22px;
    }

    .download_type {
      display: flex;
      align-items: center;
      justify-content: center;
      font-weight: 800;
      width: 52px;
      height: 52px;
      margin-bottom: 20px;

      &.apk {
        color: #ff356b;
        background: white;
        border-radius: 50%;
      }
    }

    a {
      display: flex;
      align-items: center;
      // background: @accentColor;
      border-radius: 3px;
      padding: 10px;
      cursor: pointer;
      // box-shadow: 2px 2px 2px 2px #0005;
      flex-direction: column;

      &:hover {
        background: @accentColor;
      }

      &:active {
        background: darken(@accentColor, 5%);
      }
    }
  }
}


</style>
