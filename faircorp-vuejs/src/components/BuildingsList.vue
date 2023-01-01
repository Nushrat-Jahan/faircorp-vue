<template>
  <div class="buildings-list pt-3">
    <buildings-list-item 
      v-for="building in buildings"
      v-bind:building="building"
      v-bind:key="building.id"
    >
    </buildings-list-item>
  </div>
</template>


<script>
import axios from 'axios';
import {API_HOST} from '../config';
import BuildingsListItem from './BuildingsListItem';

export default {
  components: {
    BuildingsListItem
  },
  name: 'BuildingsList',
  data() {
    return {
      buildings: []
    }
  },
  created: async function() {
    let response = await axios.get(`${API_HOST}/api/buildings`);
    let buildings= response.data;
    this.buildings = buildings;
  },
}
</script>
