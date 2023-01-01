<template>
  <div id="app">
    <header>
      <div class="title display-5 m-4">{{title}}</div>
      <div class="title display-6 m-4">Faircorp</div>
    </header>

    <section class="main-content w-50 mx-auto">
      <ul class="nav nav-pills">
        <li
          v-for="tab in tabs"
          v-bind:key="tab"
          v-bind:href="['#', {tab}]"
          v-bind:class="['nav-link', { active: currentTab === tab }]"
          data-toggle="pill"
          v-on:click="currentTab = tab"
        >
        {{tab}}
        </li>
      </ul>
      <component v-bind:is="currentTabComponent" class="tab"></component>
    </section>
  </div>
</template>

<script>

import WindowsList from './components/WindowsList.vue';
import RoomsList from './components/RoomsList.vue';
import BuildingsList from './components/BuildingsList.vue';
import ContactList from './components/ContactList.vue';
import CreateList from './components/CreateList.vue'

export default {
  name: 'App',
  components: {
    WindowsList,
    RoomsList,
    BuildingsList,
    ContactList,
    CreateList
  },
  data() {
    return {
      title: 'Smart Building Management',
      currentTab: "Windows",
      tabs: ["Windows", "Rooms", "Buildings", "Create", "Contact"]
    }
  },
  computed: {
          currentTabComponent(){
            return this.currentTab.toLowerCase() + "-list";
          }
        }
}
</script>

<style lang="scss" scoped>
#app {
  font-family: sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.title{
  color:#E00E21;
  font-weight: bold;
}
.nav-pills > .active, .nav-pills > .active:hover {
    background-color: #E00E21;
}

</style>
