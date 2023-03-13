<script setup>
import { watch, reactive, onBeforeUnmount, nextTick } from "vue";

const props = defineProps({
  map: {},
  pane: {
    default: "base",
  },
  options: {},
});
const state = reactive({
  layerCtx: null,
});

watch(
  () => props.map,
  (map) => {
    nextTick(() => {
      _initLayer(map);
    });
  },
  { immediate: true }
);

onBeforeUnmount(() => {
  _deconstructLayer();
});

const _initLayer = (map) => {
  if (map && !state.layerCtx) {
    state.layerCtx = new maptalks.TileLayer(props.pane, props.options);
    state.layerCtx.addTo(map);
  }
};

const _deconstructLayer = () => {
  if (state.layerCtx) {
    state.layerCtx.remove();
    state.layerCtx = null;
  }
};
</script>

<template></template>
