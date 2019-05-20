<template>
  <div>

    <ul id = "features">
      <li>
        <img src = "static/img/osi_symbol.png"/>
        <h3>Open Source</h3>
        <p>Fully open source and not cloud based programming.</p>
      </li>

      <li>
        <img src = "static/img/fast_setup.png"/>
        <h3>Quick setup</h3>
        <p>Install it in your Android device and you are ready to go. No need to install anything in your computer.</p>
      </li>

      <li>
        <img src = "static/img/giphy-downsized.gif"/>
        <h3>Superfast to code with</h3>
        <p>Code, run, stop, repeat without breaking your creative workflow.</p>
      </li>

      <li>
        <img src = "static/img/javascript_logo.png"/>
        <h3>Javascript-based</h3>
        <p>The language of the web supercharged with native Android functions and powerful libraries thanks to Mozilla Rhino.</p>
      </li>

      <li>
        <img src = "static/img/boards.png"/>
        <h3>Easier Peripherals</h3>
        <p>Ever wanted to connect an Arduino via OTG, bluetooth or your midi controller? Few lines of code and you are ready to go.</p>
      </li>

      <li>
        <img src = "static/img/telephon_tower.jpg"/>
        <h3>Connect to the world</h3>
        <p>OSC, Websocket, HTTP GET/POST requests, Bluetooth, NFC</p>
      </li>

      <li>
        <img src = "static/img/giphy-downsized_dog.gif"/>
        <h3>Simple to use</h3>
        <p>Simple Media, Sensor, UI & network APIs. Forget about writing hundreds of lines for basic things.</p>
      </li>

      <li>
        <img src = "static/img/phonk_libraries.png"/>
        <h3>Awesomic libraries</h3>
        <p>Processing, LibPd (Pure Data), Open Street maps</p>
      </li>

    </ul>

  </div>
</template>

<style lang = "less">
@import (reference) "../assets/variables.less";


#features {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
  grid-gap: 45px;

  h3 {
    padding: 28px 0px 10px 0px;
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

</style>
