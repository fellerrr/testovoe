<template>
  <v-app class="container">
      <v-main>
        <RenaissancePage/>
      </v-main>
    <FooterComponent/>
  </v-app>
</template>

<script>
import RenaissancePage from './components/RenaissancePage.vue';
import FooterComponent from "@/components/FooterComponent.vue";


export default {
  name: 'App',

  components: {
    FooterComponent,
    RenaissancePage,
  },

  data: () => ({
    //
  }),
};
</script>

<style scoped>
.container{
  max-width: 1216px;
  margin: 0 auto;
}
</style>