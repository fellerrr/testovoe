<template>
  <div>
    <header>
      <MenuComponent/>
      <div class="search">
        <input type="text" v-model="searchText" placeholder="Поиск по названию картины"/>
        <button>Найти</button>
      </div>
    </header>
    <h1>Картины эпохи Возрождения</h1>
    <div class="paintings">
      <CardComponent
          v-if="cards[0].title.toLowerCase().includes(searchText.toLowerCase())"
          imgSrc="/pic1.png"
          imgAlt="«Рождение Венеры» Сандро Боттичелли"
          :title="'«Рождение Венеры» Сандро Боттичелли'"
          originalPrice="2 000 000 $"
          discountedPrice="1 000 000 $"
          :alreadySold=false
      />
      <CardComponent
          v-if="cards[1].title.toLowerCase().includes(searchText.toLowerCase())"
          imgSrc="/pic2.png"
          imgAlt="«Тайная вечеря»  Леонардо да Винчи"
          :title="'«Тайная вечеря»  Леонардо да Винчи'"
          discountedPrice="3 000 000 $"
          :alreadySold=false
      />
      <CardComponent
          v-if="cards[2].title.toLowerCase().includes(searchText.toLowerCase())"
          imgSrc="/pic3.png"
          imgAlt="«Сотворение Адама» Микеланджело"
          :title="'«Сотворение Адама» Микеланджело'"
          originalPrice="6 000 000 $"
          discountedPrice="5 000 000 $"
          :alreadySold=false
      />
      <CardComponent
          v-if="cards[3].title.toLowerCase().includes(searchText.toLowerCase())"
          imgSrc="/pic4.png"
          imgAlt="«Урок анатомии»  Рембрандт"
          :title="'«Урок анатомии»  Рембрандт'"
          originalPrice="2 000 000 $"
          discountedPrice="3 000 000 $"
          :alreadySold=true
      />
      <div v-else></div>
    </div>
  </div>
</template>

<script>
import CardComponent from './CardComponent.vue';
import MenuComponent from "@/components/MenuComponent.vue";

export default {
  components: {
    CardComponent,
    MenuComponent
  },
  data() {
    return {
      searchText: "",
      cards: [
        { title: "«Рождение Венеры» Сандро Боттичелли"},
        { title: "«Тайная вечеря» Леонардо да Винчи"},
        { title: "«Сотворение Адама» Микеланджело"},
        { title: "«Урок анатомии» Рембрандт"},
      ],
    }
  }
}
</script>

<style scoped>
  h1{
    margin-top: 45px;
    margin-bottom: 39px;
    font-family: 'Merriweather',sans-serif;
    font-style: normal;
    font-weight: 700;
    font-size: 24px;
    line-height: 150%;
    color: #343030;
  }
  .paintings{
    display: flex;
    gap: 32px;
  }
  header{
    position: relative;
    display: flex;
    justify-content: flex-end;
    align-items: center;
    height: 97px;
  }

  header::after {
    content: "";
    position: absolute;
    left: -9px;
    right: -9px;
    bottom: -1px;
    height: 1px;
    background-color: #E1E1E1;
  }

  .search{
    border: 1px solid #E1E1E1;
    margin-left: 162px;
  }
  input{
    width: 294px;
    padding: 13px 0 13px 16px;
    font-family: 'Merriweather',sans-serif;
    font-style: normal;
    font-weight: 400;
    font-size: 14px;
    line-height: 150%;
    color: #343030;
  }
  input::placeholder{
    font-family: 'Merriweather',sans-serif;
    font-style: normal;
    font-weight: 400;
    font-size: 14px;
    line-height: 150%;
    color: #9F9F9F;
  }
  input:focus {
    outline: none;
  }
  .search input:focus{

    border: 1px solid #B5B5B5;
  }
  button{
    background: #403432;
    padding: 13px 36px 14px;
    font-family: 'Merriweather',sans-serif;
    font-style: normal;
    font-weight: 700;
    font-size: 14px;
    line-height: 150%;
    color: #FFFFFF;
  }
  button:hover{
    background: #776763;
  }
</style>