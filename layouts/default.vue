<template>

  <div>

    <div id = "banner">
      <div id = "title">
        <h1>Phonk!</h1>
        <h2>A self-contained creative programming tool for new and obsolete android mobile devices</h2>
      </div>


      <picture>
        <source media="(max-width: 800px)" srcset="/static/img/banner_phonk_small.png">
        <img src="/static/img/banner_phonk.png" alt="">
      </picture>

    </div>

    <div v-if = "false" class = "hero">
      <toolbar v-if = "false"></toolbar>
      <devices-code v-if = "showDevices($nuxt.$route.path)"></devices-code>
      <!--
      {{showDevices($nuxt.$route.path)}}
      {{$nuxt.$route.path}}
      -->
    </div>

    <nuxt/>

    <footer>Phonk! your phone up</footer>
  </div>

</template>

<script>
import Toolbar from '~/components/Toolbar'
import DevicesCode from '~/components/DevicesCode'

export default {
  components: {
    Toolbar,
    DevicesCode
  },
  methods: {
    showDevices: function (path) {
      return false
      // return !path.startsWith('/documentation')
    }
  }
}
</script>

<style src="~/assets/reset.css"></style>
<!--
<style src="~/assets/style.less" lang = "less"></style>
-->

<style lang = "less">
@import "../assets/variables.less";
// @import url('https://fonts.googleapis.com/css?family=Roboto+Mono:300,500,800');

* {
  box-sizing: border-box;
}

p {
  line-height: 1.5em;
}

body {
  font-family: "Roboto Mono", 'monospace';
  font-size: 16px;
  background: @backgroundColorSecondary;
  color: @textColor;
  width: 100%;
  height: 100%;
  position: relative;
  border-bottom: 2px solid @accentColor;
  // background: url("../img/tapiz.png");
}

a {
  text-decoration: inherit;
  color: inherit;
}

.hero {
  background: @backgroundColor;
  background-image: url('~/static/static/img/drawing_phonk.svg');
  background-repeat: no-repeat;
  background-size: 180%;
  background-position: 55% 38%;
  background-attachment: fixed;
  padding: 32px 30px;
}

@media screen and (max-width: 800px) {
  #banner {
    display: flex;
    flex-direction: column;
    background: #e0e0e0;

    #title {
      position: static !important;
      width: 100% !important;
      max-width: 100% !important;
      background: #e0e0e0;
      padding: 35px;
      padding-bottom: 0;
      font-size: calc(5vmin) !important;
    }

    picture {
      margin-bottom: -40px;
      padding: 10px 20px;
    }

  }
}

#banner {

  #title {
    position: absolute;
    top: calc(4.5vw);
    left: calc(4.5vw);
    width: 25%;
    max-width: 28%;
    font-size: 2vw;
  }

  h1 {
    font-weight: 800;
    font-size: 2em;
    margin-bottom: 10px;
  }

  h2 {
    line-height: 1.5em;
  }

  img {
    width: 100%;
  }
}

#container {
  padding: 20px;
  max-width: 1080px;
  margin: 0 auto;
  display: flex;
  flex-flow: column;
  position: relative;
}


@media screen and (max-width: 700px) {
  ul {
    flex-direction: column;
    font-size: 1.2em;
  }
}

@media screen and (max-width: 470px) {
  nav {
    display: none;
  }

  h2 {
    font-size: 1em;
    max-width: 82%;
  }

  #download {
    flex-direction: column !important;
  }

  #webbrowser {
    .url {
      padding: 1px !important;
    }
  }

  #features {
    li {
      width: 100% !important;
    }

    img {
      width: 100% !important;
      height: unset !important;
      object-fit: cover;
    }
  }
}

h3 {
  font-weight: 500;
}

#devices {
  max-width: 800px;
  margin: 20px auto;
  display: flex;
  flex-flow: row wrap;
  align-items: flex-end;
  align-self: center;
  align-content: center;
  justify-content: space-around;
}

.device {
  box-shadow: 0px 0px 7px 0px rgba(0, 0, 0, 0.4);
  border: 1px solid rgba(0, 0, 0, 0.2);
  box-sizing: content-box;

  img {
    width: 100%;
    border-radius: 2px;
  }
}


@keyframes initAnim {
    0% {
        transform: translateY(-40px);
        opacity: 0;
    }
    100% {
        transform: translateY(0);
        opacity: 1;
    }
}


#webbrowser {
  position: relative;
  background: rgba(238, 238, 238, 1);
  width: 91%;
  animation: 0.4s ease-out 0s 1 normal initAnim;
  animation-fill-mode: backwards;
  animation-delay: 0.3s;
  overflow: hidden;

  #code {
    position: absolute;
    top: 19%;
    left: 3%;
    color: white;
    font-family: Courier;
    width: 58%;
    white-space: pre-wrap;
    line-height: ~"calc(0.3em + 1.2vmin)";
    font-size: ~"calc(0.1em + 1.2vmin)";
    font-family: 'Roboto Mono';
  }

   img {
    // padding: 0.5%;
    // padding-top: 0%;
    border-radius: 0px;
  }

   .url {
      padding: 3px;
      font-size: ~"calc(3px + 0.5vw)";
      color: #565656;
      background: rgba(255, 255, 255, 0.79);
      max-width: 55%;
      margin: 4px auto;
      border-radius: 22px;
      text-align: center;
      font-weight: 300;
      font-family: "Roboto Mono";
  }
}

#phone {
  * {
    transition: all 0.5s ease-in-out;
  }
  background: #3a3a3a;
  width: 21%;
  margin-left: -15%;
  border-radius: 2px;
  padding: 0.1%;
  animation: 0.4s ease-out 0s 1 normal initAnim;
  animation-fill-mode: backwards;
  z-index: 2;

  .img_container {
    position: relative;
    padding-top: 5%;
    padding-bottom: 0%;
  }
}

#download {
  display: flex;
  align-self: center;
  flex: 1;
  margin: 70px 0;
  font-size: 1.5em;
  text-overflow: ellipsis;
  align-content: center;
  align-items: center;
  flex-flow: initial;
  text-transform: uppercase;

  a {
    background: transparent;
    padding: 18px 22px;
    margin: 8px;
    border-radius: 0px;
    color: white;
    text-decoration: none;
    font-weight: 800;
    color: @textColorSecondary;
    background: @accentColor;
    box-shadow: 2px 2px 2px 1px #0003;
  }

  a:hover {
    background: lighten(@accentColor, 10%);
    color: white;
  }
}

#features {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  grid-gap: 45px;

  h3 {
    padding: 28px 0px 16px 0px;
    font-size: 1.2em;
    color: #333;
  }

  p {
    font-size: 0.8em;
    line-height: 1.4em;
    font-weight: 400;
  }

  li {
    margin: 22px 0;
  }

  img {
    background: white;
    // width: 200px;
    height: 300px;
    width: 100%;
    outline: none;
    object-fit: cover;
    box-shadow: 0 0 1px 1px rgba(0, 0, 0, 0.1);
  }
}

footer {
  color: white;
  font-weight: 800;
  background: @accentColor;
  height: 100px;
  font-size: 1em;
  text-align: center;
  padding-top: 50px;
}

#app {
  position: absolute;
  z-index: 2;
  opacity: 0;
  width: 100%;
  object-fit: inherit;
  transform: scale3d(0.8, 0.8, 0.8);
}

#so {
  transform: scale3d(1, 1, 1);
}

.qq {
  #app {
    opacity: 1 !important;
    transform: scale3d(1, 1, 1);
  }

  #so {
    opacity: 0 !important;
    transform: scale3d(0.8, 0.8, 0.8);
  }
}

#drawing {
  display: none;
  position: absolute;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
}
</style>
