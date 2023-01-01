<template>
    <div class="building border border-secondary rounded shadow-sm p-2 mb-2 bg-white" :class="{expanded: isExpanded}">
        <div class="top-row d-flex" @click="getRooms">
            <div class="building-name fw-bold pe-3">{{building.id}}</div>
            <div class="building-out-temp text-muted">Outside Temperature: {{building.outsideTemperature}}&#x2103;</div>

            <div class="expand-button ms-auto">
            {{ isExpanded ? '&#9660;' : '&#9658;' }}
            </div>
        </div>

        <template v-if="isExpanded">
          <button type="button" class="btn p-2 btn-danger me-2" v-on:click="deleteBuilding">Delete Building</button>
            <hr/>

            <div class="details justify-content-around m-10">
                <div class="rooms-list pt-3">
                    <rooms-list-item 
                        v-for="room in rooms"
                        v-bind:room="room"
                        v-bind:key="room.id"
                    >
                    </rooms-list-item>
                </div>
            </div>
        </template>
    </div>

</template>

<script>

import axios from 'axios';
import { API_HOST } from '../config';
import RoomsListItem from './RoomsListItem.vue'

export default {
    name: 'BuildingsListItem',
    components:{
        RoomsListItem
    },
    props: ['building'],
    data() {
        return {
            isExpanded: false,
            isShow: false,
            currentTemp: 0,
            targetTemp: 0,
            rooms:[]
        }
    }, 
    methods: {
        async getRooms(){
            this.isExpanded = !this.isExpanded;
            let response = await axios.get(`${API_HOST}/api/rooms/buildings/${this.building.id}`);
            this.rooms = response.data;
        },
      async deleteBuilding(){
        await axios.delete(`${API_HOST}/api/buildings/${this.building.id}`);
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

.building {
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
