<template>
  <div class="room border border-secondary rounded shadow-sm p-2 mb-2 bg-white" :class="{expanded: isExpanded}">
    <div class="top-row d-flex" @click="toggleExpand">
      <div class="room-name fw-bold pe-3">{{room.name}}</div>
      <div class="room-floor text-muted">floor&#35;{{room.floor}}</div>
      <div class="expand-button ms-auto">
        {{ isExpanded ? '&#9660;' : '&#9658;' }}
      </div>
    </div>
    <template v-if="isExpanded">
      <hr/>
      <div class="details d-flex justify-content-around m-10">
        <div class="p-2">Current Temperature: {{room.currentTemperature}} &#x2103;</div>
        <div class="p-2">Target Temperature: {{room.targetTemperature}} &#x2103;</div>
        <button type="button" class="btn p-2 btn-danger me-2" v-on:click="deleteRoom">Delete room</button>
      </div>
    </template>
  </div>
</template>

<script>


import axios from "axios";
import {API_HOST} from "@/config";

export default {
  name: 'RoomsListItem',
  props: ['room'],
  data() {
    return {
      isExpanded: false,
      isShow: false,
      currentTemp: 0,
      targetTemp: 0,
    }
  }, 
  methods: {
    toggleExpand() {
      this.isExpanded = !this.isExpanded;
    },
    showWindows(){
      this.isShow = !this.isShow;
      alert(this.room.name)
    },
    async deleteRoom(){
      await axios.delete(`${API_HOST}/api/rooms/${this.room.id}`);
      location.reload()
    },
  }
}
</script>

<style lang="scss" scoped>

.open-status {
  .icon {
    position: relative;
  }

  &.open {
    color: #198754;
    .icon {
      font-size: 12px;
      top: -3px;
    }
  }

  &.closed {
    color: #dc3545;
  }
}

.room {
  .top-row {
    cursor: pointer;
  }
}
.details>.p-2{
  background-color: #dc3545;
  color: azure;
  border-radius: 0.2em;
}
</style>
