<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          :src="url"
          transition="scale-transition"
          width="40"
        />

        <h1>Países</h1>
      </div>

      <v-spacer></v-spacer>

    </v-app-bar>

    <v-main>
      <ListaPaises/>
    </v-main>
  </v-app>
</template>

<script>
import ListaPaises from './components/ListaPaises';

export default {
  name: 'App',

  components: {
    ListaPaises,
  },

  data: () => ({
    url: 'https://static.vecteezy.com/system/resources/previews/001/197/992/non_2x/world-png.png'
  }),
};
</script>
