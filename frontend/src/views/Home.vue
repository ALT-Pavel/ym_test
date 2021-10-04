<template>
  <yandex-map :coords="coords" @click="onClick">
    <ymap-marker 
      marker-id="123" 
      :coords="coords"
      :balloon-template="balloonTemplate"
    />
  </yandex-map>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import axios from 'axios';
import { yandexMap, ymapMarker } from 'vue-yandex-maps';

Component({
  components: {
    yandexMap,
    ymapMarker
  },
})
export default {
  data: () => ({
    coords: [54, 39],
  }),
  computed: {
    balloonTemplate() {
      return `
        <h1 class="red">Hi, everyone!</h1>
        <p>I am here: ${this.coords}</p>
        <img src="http://via.placeholder.com/350x150">
      `
    }
  },
  methods: {
    onClick(e) {
      this.coords = e.get('coords');
    }
  }  
}
</script>
