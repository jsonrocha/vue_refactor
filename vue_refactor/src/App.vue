<template>
  <div id="app">
    <HelloWorld msg="Pick a color.  Any color...In Vue.js!"/>
    <section>
        Hue: {{this.hue}}
      <input type="range" min="0" max="360" v-on:input="HueUpdated" v-model="hue"/>
      </section>
      <section>
        Lightness: {{this.lightness}}
      <input type="range" min="0" max="100" v-on:input="LightnessUpdated" v-model="lightness"/>
      </section>
      <section>
        Saturation: {{this.saturation}}
      <input type="range" min="0" max="100" v-on:input="SaturationUpdated" v-model="saturation"/>
      </section>
  <section id="color-box" :style="backgroundColor"> 
  </section>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
export default {
  name: "app",
  // name: "color-box",
  components: {
    HelloWorld
  },
  
  data: function() {
    return {
      hue: 180,
      saturation: 50,
      lightness: 50,
    };
  },
  computed:{
    backgroundColor:function(){
      return `background-color : hsla(${this.hue}, ${this.saturation}%, ${this.lightness}%)`
    }
  },
  methods: {
    HueUpdated: function() {
      console.log("Hue was updated", this.hue);
    },
    SaturationUpdated: function() {
      console.log("Saturation was updated", this.saturation);
    },
    LightnessUpdated: function() {
      console.log("Lightness was updated", this.lightness);
    }
  }
}
</script>

<style>
section {
  margin-top: 30px;
}

#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 30px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
#color-box {
  width: 300px;
  height: 300px;
  margin-top: 30px;
}
</style>