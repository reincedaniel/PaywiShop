<template>
  <q-page class="flex column">
    <div class="col">
      <q-bar style="height:47px" dense class="bg-grey-9 text-white text-bold q-mb-lg">
        <q-icon style="padding-left: 9px" size="sm" class="q-pr-md" name="roofing" />
        <div>Início</div>
        <q-space />

        <q-toolbar>
          <q-toolbar-title class="text-center">
          </q-toolbar-title>
        </q-toolbar>

      </q-bar>
    </div>
    <!-- <div class="col q-pt-lg q-px-md">
      <q-input
        v-model="search"
        placeholder="Search"
        
        borderless
        >

        <template v-slot:before>
          <q-icon
          @click="getLocation()"
            name="my_location" />
        </template>

        <template v-slot:append>
          <q-btn round dense flat icon="search" />
        </template>
      </q-input>
    </div> -->





  </q-page>
</template>

<script>
import axios from 'axios'
export default {
  name: 'PageIndex',
  data(){
    return{
     
    }
  },
}
</script>

