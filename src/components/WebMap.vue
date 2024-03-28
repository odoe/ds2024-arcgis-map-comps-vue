<script setup lang="ts">
import { defineCustomElements } from '@arcgis/map-components/dist/loader'
defineCustomElements(window)

function onReady(event: any) {
  console.log('The map is ready', event.target)
}

const props = defineProps({
  popup: {
    type: Object,
    default: () => {
      return {
        dockEnabled: true,
        dockOptions: {
          position: 'bottom-right',
          breakpoint: false
        }
      }
    }
  },
  theme: {
    type: Object,
    default: () => {
      return {
        accentColor: 'purple',
        textColor: [125, 255, 13, 0.9]
      }
    }
  }
})
</script>

<template>
  <arcgis-map item-id="d5dda743788a4b0688fe48f43ae7beb9" @arcgisViewReadyChange="onReady" :popup="props.popup"
    :theme="props.theme">
    <arcgis-search position="top-right" />
    <arcgis-expand position="bottom-left">
      <arcgis-area-measurement-2d />
    </arcgis-expand>
  </arcgis-map>
</template>

<style>
@import '@arcgis/core/assets/esri/themes/dark/main.css';
</style>
