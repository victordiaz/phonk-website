<template>
  <div class="toolbar">
    <div id = "header">
      <h1><nuxt-link to = "/">phonk!</nuxt-link></h1>
      <h2>Bits of creative programming for Android-based devices</h2>
    </div>

    <nav>
      <ul style="display: flex;">
        <!--
        <li id = "link_download"><a href = "#downloads">Download</a></li>
        <li id = "link_documentation"><nuxt-link to = "/documentation">Documentation</nuxt-link></li>
        <li id = "link_contribute"><a href = "">Contribute</a></li>
        <li id = "link_about"><a href = "">About</a></li>
        -->
      </ul>
    </nav>
  </div>
</template>

<style lang = "less">
@import "../assets/variables.less";

.toolbar {
  display: flex;
  color: white;
  font-weight: 500;

  ul {
    margin-top: 6px;
    #link_download:hover { border-bottom: 2px solid @accentColor }
    #link_documentation:hover { border-bottom: 2px solid @accentColorSecondary }
    #link_contribute:hover { border-bottom: 2px solid @accentColorSecondary }
    #link_about:hover { border-bottom: 2px solid @accentColorTerciary }

    li {
      margin-right: 10px;
      padding-bottom: 2px;
    }

    a {
      color: white;
      text-decoration: none;
    }
  }
}

nav {
  margin-top: 25px;
}


#header {
  flex: 1;
  margin-bottom: 4vh;
}

h1 {
  font-family: 'Roboto Condensed';
  font-size: 5.5em;
  font-weight: 700;
  margin-bottom: 12px;
  line-height: 1.1em;
  letter-spacing: 2px;
  color: @textColorSecondary;
}

h2 {
  font-family: 'Roboto Mono';
  color: @textColorSecondary;
  line-height: 1.2em;
  font-size: 1.2em;
  // font-size: 2.2vw;
  font-weight: 300;
}

</style>
