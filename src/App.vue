<template>
  <v-app>
    <v-app-bar
        app
        color="orange"
        dark
    >
      <div class="d-flex align-center">
        <span class="text-uppercase">Proceeding Tool</span>
      </div>
    </v-app-bar>

    <v-main>
      <Form/>
    </v-main>
  </v-app>
</template>

<script>
import Form from './components/Form';

export default {
  name: 'App',

  components: {
    Form,
  },

  data: () => ({
    //
  }),
};
</script>
