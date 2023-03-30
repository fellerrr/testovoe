<template>
  <div class="card" :class="{ 'alreadySoldCard': alreadySold}" >
    <img :src="imgSrc" :alt="imgAlt" @click="openModal">
    <h2 @click="openModal">{{ title }}</h2>
    <h3 :class="{ 'sold': alreadySold, 'alreadySold': !alreadySold}">Продана на аукционе</h3>
    <div :class="{ 'BlockPrice': !alreadySold, 'alreadySold': alreadySold}">
      <div class="price">
        <h5>{{ originalPrice }}</h5>
        <h3>{{ discountedPrice }}</h3>
      </div>
      <button :class="{ 'buy': !inCart, 'inCart': inCart, 'is-processing': isProcessing}"
              @click="handleClick">
        {{ buttonText }}
      </button>
      <v-progress-circular
          :class="{ 'noLoading': !isProcessing, 'loading': isProcessing}"
          :size="32"
          :width="2"
          color="brown"
          indeterminate
      >
      </v-progress-circular>
      <ProductModal
          :class="{ 'noShowModal': !showModal, 'showModal': showModal}"
          @closeModal="closeModal"
          :title=title
          :price=discountedPrice
          description="Lorem Ipsum is a placeholder text commonly used in the graphic, print and placeholder text commonly used in the graphic, print and web design web design placeholder text commonly used in the graphic, print and web design industries. It is used to fill the space where the final copy will eventually go."
      />
    </div>
  </div>
</template>

<script>
import ProductModal from './ProductModal.vue'
export default {
  components: {
    ProductModal
  },
  props: {
    imgSrc: {
      type: String,
          required: true,
    },
    imgAlt: {
      type: String,
          required: true,
    },
    title: {
      type: String,
          required: true,
    },
    originalPrice: {
      type: String,
    },
    discountedPrice: {
      type: String,
          required: true,
    },
    alreadySold: {
      type: Boolean,
      required: true,
    }
},
data() {
  return {
    buttonText: 'Купить',
    isProcessing: false,
    inCart: false,
    showModal: false
  };
},

methods: {
  handleClick() {
    this.isProcessing = true;
    this.buttonText = '';
    setTimeout(() => {
      this.isProcessing = false;
      this.inCart = true;
      this.buttonText = '✓ В корзине';
      localStorage.setItem(`${this.title}-inCart`, 'true');
    }, 2000);
  },
  openModal() {
    this.showModal = true;
  },
  closeModal() {
    this.showModal = false;
  }
},
  mounted() {
    this.inCart = localStorage.getItem(`${this.title}-inCart`) === 'true';
    this.buttonText = this.inCart ? '✓ В корзине' : 'Купить';
  },
};
</script>

<style scoped>
.card{
  max-width: 280px;
  margin-bottom: 320px;
  border: 1px solid #E1E1E1;
  /*position: relative;*/
}
img{
  cursor: pointer;
}
h2{
  margin: 20px 0 22px 24px;
  cursor: pointer;
}
 .BlockPrice{
   display: flex;
   justify-content: space-between;
   align-items: center;
   margin: 0 24px 24px 0;
 }

 .price{
   display: flex;
   flex-direction: column;
   justify-content: center;
   margin-left: 24px;
   height: 48px;

 }
 h5{
   font-family: 'Merriweather',sans-serif;
   font-style: normal;
   font-weight: 300;
   font-size: 14px;
   line-height: 150%;

   text-decoration-line: line-through;

   color: #A0A0A0;

 }
 h3{


   font-family: 'Merriweather',sans-serif;
   font-style: normal;
   font-weight: 700;
   font-size: 16px;
   line-height: 150%;

   color: #343030;


 }
 .buy{
   padding: 14px 30px 13px 31px;

   background: #382E2B;
   font-family: 'Merriweather',sans-serif;
   font-style: normal;
   font-weight: 700;
   font-size: 14px;
   line-height: 150%;
    color: #F4F6F9;
 }
.buy:hover{
  background: #776763;
}
.is-processing {
  /*background-color:red;*/
  display: none;
}
.inCart{
  padding: 14px 9px 13px 8px;

  background: #5B3A32;
  font-family: 'Merriweather', sans-serif;
  font-style: normal;
  font-weight: 700;
  font-size: 14px;
  line-height: 150%;
  color: #F4F6F9;

  pointer-events: none;
}
.noLoading, .alreadySold, .noShowModal{
  display: none;
}
.showModal{

  display: block;
}
.loading{
  display: block;
  margin-right: 40px;
}
.sold{
  display: block;
  font-family: 'Merriweather', sans-serif;
  font-style: normal;
  font-weight: 700;
  font-size: 16px;
  line-height: 150%;
  color: #343030;
  margin-left: 24px;
  margin-top: 34px;

}
.alreadySoldCard{
  opacity: 0.5;
}
</style>