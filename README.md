# A demo, create the Vue3 Map component with maptalks.js

## Introduction

Here is a simple demo, create the Map and the Layer component with maptalks.js and the Vue3 Framework.

> - The Progressive JavaScript Framework
>   - https://vuejs.org/
> - An open-source javascript library for integrated 2D/3D maps.
>   - https://maptalks.org/

## Code examples

I have created two simple components. The first is the `TMap`, which is a base map context without any layers. And then, I created a slot, which is an important notion in the `Vue.js` framework, that allows the `TMap` component exposes the map context to its sub-components.

The sub-component here, which name is `TTileLayer`, should be put inside the `<template>`, which could get the map context outside and manage its own life cycle. Thus, we could use the `v-if` option to control the layer. That would be nice.

```html
<TMap v-if="state.toggleMap" map-id="DemoMap1" v-slot="{ map }">
  <template>
    <TTileLayer v-if="state.toggleLayer" :map="map" :options="tileLayerOSM" />
  </template>
</TMap>
```

## How to use

I recommend you manage the project's dependencies by using the `Yarn` tool.

```bash
yarn
yarn dev

-------------------

  VITE v4.1.4  ready in 273 ms

  ➜  Local:   http://127.0.0.1:5173/
  ➜  Network: use --host to expose
  ➜  press h to show help

```

And you would see the result on your broswer.

## Furthermore

You could try your layers this way, and if you have any questions. It would be regardful for me to recieve your comments.
