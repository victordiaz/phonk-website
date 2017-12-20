<template>
  <!--
      <meta name="viewport" content="initial-scale=1, minimum-scale=1.0, maximum-scale=1.0">
      <title>phonk! bits of creative programming for Android devices</title>
      <meta name="description" content="Self-contained creative coding framework for Android devices">
      <link href="https://fonts.googleapis.com/css?family=Roboto+Mono:100,300,400,500,700|Roboto:400,500,700|Roboto+Condensed:700" rel="stylesheet">
  -->

  <div>
    <div class = "hero">
      <toolbar></toolbar>
      <devices-code v-if = "showDevices($nuxt.$route.path)"></devices-code>
      <!--
      {{showDevices($nuxt.$route.path)}}
      {{$nuxt.$route.path}}
      -->

    </div>

    <nuxt/>

    <footer>Phonk!</footer>
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
      return !path.startsWith('/documentation')
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

* {
  box-sizing: border-box;
}

body {
  font-family: "Roboto", sans-serif;
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

#container {
  padding: 20px;
  max-width: 960px;
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

.construction {
  position: absolute;
  right: 0;
  text-align: center;
  display: flex;
  align-items: center;

  p {
    margin-right: 12px;
    font-weight: 600;
    text-decoration: underline;
  }

  img {
    width: 50px;
    height: 50px;
  }
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
  margin: 30px 0;
  font-size: 1.5em;
  text-overflow: ellipsis;
  align-content: center;
  align-items: center;
  flex-flow: initial;

  a {
    background: transparent;
    padding: 8px 12px;
    margin: 8px;
    border-radius: 0px;
    color: white;
    text-decoration: none;
    font-weight: 600;
    color: @textColorSecondary;
    background: @accentColor;
  }

  a:hover {
    background: lighten(@accentColor, 10%);
    color: white;
  }
}

#features {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  grid-gap: 30px;

  h3, p {
    padding: 8px 0;
  }

  p {
    font-size: 0.8em;
    font-weight: 100;
    line-height: 1.4em;
  }

  li {
    margin-top: 22px;
  }

  img {
    background: white;
    // width: 200px;
    // height: 200px;
    width: 100%;
    outline: none;
    object-fit: cover;
    box-shadow: 0 0 1px 1px rgba(0, 0, 0, 0.1);
  }
}

footer {
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
