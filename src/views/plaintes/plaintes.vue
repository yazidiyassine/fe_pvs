<template>
<div>
  <v-tabs
      v-model="tab"
       active-class="active1"
       height="35px"
    >
    <v-tab
      class="text-h6 mx-10"
      >
      <v-icon right>mdi-note-multiple-outline</v-icon>
       إضافة شكاية
      </v-tab>
      <v-tab
      class="text-h7 mx-10"
      
      >
      <v-icon right>mdi-police-badge-outline</v-icon>
      بحث عن شكاية
      </v-tab>
       </v-tabs>
    <v-tabs-items v-model="tab">
      <v-tab-item
      >
      <ajoutplainte></ajoutplainte>
      </v-tab-item>
      <v-tab-item
      >
      <chercheplainte />
      </v-tab-item>
      </v-tabs-items>
  </div>
</template>

<script>
import ajoutplainte from '@/components/plaintes/ajout_plainte.vue'
import chercheplainte from '@/components/plaintes/cherche_plainte.vue'
  export default {
    components: {
      ajoutplainte,
      chercheplainte
    },
    data() {
      return {
        tab: null,
      }
    }
  }
</script>
<style>
  .active1 {
       color: #222222 !important;
       background: -webkit-linear-gradient(to right, #4ca2cd, #67B26F) !important; 
       background: linear-gradient(to right, #4ca2cd, #67B26F) !important; 

    }
</style>
