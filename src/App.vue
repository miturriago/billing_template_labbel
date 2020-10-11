<template>
  <v-app>
    <v-app-bar app color="white" dark>
      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="https://res.cloudinary.com/dos13qenv/image/upload/q_auto:low/v1595388590/Labbel/logo1_rhi81q.png"
          transition="scale-transition"
          width="100"
        />

        <v-img
          alt="Vuetify Name"
          class="shrink mt-1 hidden-sm-and-down"
          contain
          min-width="100"
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-name-dark.png"
          width="100"
        />
      </div>
    </v-app-bar>

    <v-main>
      <Body />
    </v-main>
  </v-app>
</template>

<script>
import Body from "./components/Body";

export default {
  name: "App",

  components: {
    Body,
  },

  data: () => ({
    //
  }),
};
</script>
