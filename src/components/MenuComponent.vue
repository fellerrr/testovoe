<template>
  <nav>
    <ul>
      <li>Каталог</li>
      <li>Доставка</li>
      <li>Оплата</li>
      <li>Контакты</li>
      <li>О компании</li>
    </ul>
  </nav>
</template>

<script>
export default {
  name: "MenuComponent"
}
</script>

<style scoped>
ul{
  display: flex;
  gap: 48px;

  justify-content: center;
}
li{
  font-family: 'Merriweather',sans-serif;
  font-style: normal;
  font-weight: 400;
  font-size: 14px;
  line-height: 150%;
  color: #343030;

  cursor: pointer;
}
</style>