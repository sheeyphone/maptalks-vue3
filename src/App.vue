<script setup>
import { reactive } from "vue";
import TMap from "./components/TMap.vue";
import TTileLayer from "./components/TTileLayer.vue";

const tileLayerConfig = {
  urlTemplate: "http://{s}.basemaps.cartocdn.com/light_all/{z}/{x}/{y}.png",
  subdomains: ["a", "b", "c", "d"],
  attribution:
    '&copy; <a href="http://www.osm.org/copyright">OSM</a> contributors, ' +
    '&copy; <a href="https://carto.com/attributions">CARTO</a>',
};

const state = reactive({
  toggleMap: true,
  toggleLayer: true,
});

const clickToggleMap = () => {
  state.toggleMap = !state.toggleMap;
};
const clickToggleLayer = () => {
  state.toggleLayer = !state.toggleLayer;
};
</script>

<template>
  <div class="App">
    <TMap v-if="state.toggleMap" map-id="DemoMap1" v-slot="{ map }">
      <template>
        <TTileLayer
          v-if="state.toggleLayer"
          :map="map"
          :options="tileLayerOSM"
        />
      </template>
    </TMap>
    <div
      class="Btn"
      :class="{ BtnActive: state.toggleMap }"
      @click="clickToggleMap"
    >
      toggleMap
    </div>
    <div
      class="Btn BtnLayer"
      :class="{ BtnActive: state.toggleLayer }"
      @click="clickToggleLayer"
    >
      toggleLayer
    </div>
  </div>
</template>

<style lang="scss" scoped>
.App {
  position: relative;
  height: 100%;
  width: 100%;

  .Btn {
    position: absolute;
    top: 15px;
    left: 15px;
    display: inline-block;
    z-index: 1100;
    border: 1px solid #000;
    background-color: #fff9;
    border-radius: 5px;
    padding: 5px 10px;
    cursor: pointer;
    user-select: none;
  }
  .BtnLayer {
    top: 55px;
  }
  .BtnActive {
    background-color: rgb(150, 0, 0, 0.3);
  }
}
</style>
