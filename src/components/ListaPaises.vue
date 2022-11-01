<template>
  <v-container>
    
    <v-card
      class="mx-auto"
      max-width="100%"
      outlined
      v-for="(pais, i) in paisesListados"
          :key="i"
      
      >
    
        <v-list-item three-line>
        <v-list-item-content>
        
        <v-list-item-title class="text-h5 mb-1">
        {{pais.nome}}
          
        </v-list-item-title>
        <v-list-item-subtitle>{{pais.capital}}</v-list-item-subtitle>
        <a :href="pais.maps" target="_blank">Google Maps</a>
      </v-list-item-content>

      
      <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          :src="pais.urlBandeira"
          
          transition="scale-transition"
          width="120"
        />
      
    
    
    </v-list-item>
    
  
  </v-card>
  <br>
    
  </v-container>
</template>

<script>
import axios from 'axios';
import { PAIS_URL } from '@/data/enviroment';
  export default {
    name: 'ListaPaises',

    data: () => ({
      
      paisesListados: [],
      urlBase: PAIS_URL,

      
    }),
    mounted(){
      this.getListaPaises();

    },
    methods: {
      async getListaPaises(){
        const resp = await axios.get(`${this.urlBase}`);
        var todosPaises = resp.data;
        for(var i = 0; Object.keys(todosPaises).length - 1; i++ ){
            var pais = {
              nome : todosPaises[i].name.official,
              capital: todosPaises[i].capital[0],
              maps : todosPaises[i].maps.googleMaps,
              urlBandeira : todosPaises[i].flags.png
            };
            this.paisesListados.push(pais);   
        }  
      },

    },


  }
</script>
