<script setup>
import { reactive } from "vue";

const props = defineProps({
  mapId: {
    type: String,
  },
  options: {
    default: {
      center: [112.5, 22.5],
      zoom: 6,
    },
  },
});
const state = reactive({
  mapCtx: null,
});

const vMap = {
  mounted() {
    _initMap();
  },
  unmounted() {
    _deconstructMap();
  },
};

const _initMap = () => {
  if (!state.mapCtx) {
    state.mapCtx = new maptalks.Map(props.mapId, props.options);
  }
};
const _deconstructMap = () => {
  if (state.mapCtx) {
    state.mapCtx.remove();
    state.mapCtx = null;
  }
};
</script>

<template>
  <div :id="mapId" class="TMap" v-map>
    <slot :map="state.mapCtx"></slot>
  </div>
</template>

<style lang="scss">
.TMap {
  position: relative;
  height: 100%;
  width: 100%;
}
</style>
