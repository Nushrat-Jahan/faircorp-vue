<template>
  <div>
    <div class="create border border-secondary rounded shadow-sm p-2 mb-2 mt-4 bg-white expanded">
      <div class="top-row d-flex">
        <div class="create-window fw-bold pe-3">Create window</div>
      </div>
      <hr/>
      <template>
        <form>
          <input type="text" placeholder="Window name" class="form-control form-control mb-2" v-model="windowName">
          <div v-for="room in rooms" v-bind:room="room" v-bind:key="room.id"  class="form-check">
            <label class="form-check-label">
              <input type="radio" class="form-check-input" name="roomOption" v-bind:value="room.id" v-model="roomNumber">{{room.name}}
            </label>
          </div>
          <div class="details d-flex">
            <button type="button" class="addWindow btn p-2 btn-primary me-2" v-on:click="createWindow" v-bind:disabled="!windowName || !roomNumber">Create window</button>
          </div>
        </form>
      </template>
    </div>
    <div class="create border border-secondary rounded shadow-sm p-2 mb-2 mt-4 bg-white expanded">
      <div class="top-row d-flex">
        <div class="create-window fw-bold pe-3">Create Room</div>
      </div>
      <hr/>
      <template>
        <form>
          <input type="text" placeholder="Room name" class="form-control form-control mb-2" v-model="roomName">
          <input type="number" placeholder="Floor number"  class="form-control form-control mb-2" v-model="floor">
          <input type="number" placeholder="Current Temperature" class="form-control form-control mb-2" v-model="currentTemperature">
          <input type="number" placeholder="Target Temperature" class="form-control form-control mb-2" v-model="targetTemperature">
          <div class="details d-flex">
            <button type="button" class="addWindow btn p-2 btn-primary me-2" v-on:click="createRoom" v-bind:disabled="!roomName || !floor || !currentTemperature || !targetTemperature ">Create Room</button>
          </div>
        </form>
      </template>
    </div>
  </div>
</template>


<script>
import axios from 'axios';
import { API_HOST } from '../config';

export default {
  name: 'CreateList',
  data(){
    return {
      rooms: [],
      roomNumber: null,
      windowName: null,
      roomName : null,
      floor : 0,
      currentTemperature : 0,
      targetTemperature : 0
    }
  },

  created: async function(){

    let response = await axios.get(`${API_HOST}/api/rooms`);
    this.rooms = response.data;
  },

  methods:{
    async createWindow(){
      let postData = {
        "name": this.windowName,
        "roomId":this.roomNumber ,
        "windowStatus": "CLOSED"
      };
      await axios.post(`${API_HOST}/api/windows`, postData);
      location.reload()
    },
    async createRoom(){
      let postDataRoom = {
        "currentTemperature" : parseInt(this.currentTemperature),
        "floor": parseInt(this.floor),
        "name": this.roomName,
        "targetTemperature" : parseInt(this.targetTemperature)
      }
      await axios.post(`${API_HOST}api/rooms`, postDataRoom);
      location.reload()
    }
  }

}
</script>

<style lang="scss" scoped>
.create{
  .top-row {
    cursor: pointer;
  }
}

.addWindow.btn, .addWindow.btn:active{
  color: white;
  background-color: #dc3545;
  border-color: #dc3545;
}

.create {
  .top-row {
    cursor: pointer;
  }
}
</style>