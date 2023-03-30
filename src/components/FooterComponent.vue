<template>
  <footer>
    <MenuComponent/>
    <div class="contacts">
      <div class="tel">
        <v-icon>mdi-phone</v-icon>
        <h5>+7 (812) 555-55-55</h5>
      </div>
      <div class="address">
        <v-icon>mdi-map-marker</v-icon>
        <h5>г. Санкт-Петербург, ул. Ефимова, 3</h5>
      </div>
    </div>
  </footer>

</template>

<script setup>

import MenuComponent from "@/components/MenuComponent.vue";

</script>

<style scoped>
 footer{
   padding-left: 70px;
   background: #ECEAEA;
   height: 96px;
   display: flex;
   justify-content: space-between;
   align-items: center;
 }
 .contacts{
   display: flex;
   justify-content: center;
   align-items: center;
   gap: 51px;
 }
 h5{
   font-family: 'Merriweather',sans-serif;
   font-style: normal;
   font-weight: 400;
   font-size: 14px;
   line-height: 150%;
   color: #555555;
 }
 .tel,.address{
   display:flex;
   align-items: center;
   gap: 8px;
 }
</style>