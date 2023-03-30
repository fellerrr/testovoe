
<template>
  <div class="modal">
    <div class="modal-content">
      <h2>{{ title }}</h2>
      <Carousel>
        <Slide v-for="slide in slides" :key="slide.id">

          <img :src="slide.src" alt="" eager>
        </Slide>
      </Carousel>
      <p>{{ description }}</p>
      <p>{{ price }}</p>
      <button @click="$emit('closeModal')">Close</button>
    </div>
  </div>
</template>

<script>
import { Carousel, Slide } from 'vue-carousel'
export default {
  components: {
    Carousel,
    Slide
  },
  props: {
    title: {
      type: String
    },
    description: {
      type: String
    },
    price: {
      type: String
    }
  },
  data() {
    return {
      slides: [
        {id: 1, src: 'pic1.png'},
        {id: 2, src: 'pic2.png'},
        {id: 3, src: 'pic3.png'}
      ]
    }
  }
}

</script>

<style scoped>

.modal{
  z-index: 1;
  width: 90vw;
  height: 100vh;
  background-color: #382E2B80;
  position: absolute;
  top: 0;
  left: 0;
}
.modal-content{
  width: 70%;
  margin: 20px auto;
  background-color: #E1E1E1;
  display: flex;
  flex-direction: column;
  gap: 20px;
  align-items: center;
  justify-content: center;
  padding: 30px;
}
h2{
  color: red;
}
</style>