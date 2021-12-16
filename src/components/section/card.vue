<template>
  <div>
    <img :src="info.poster" alt="" />
    <h2>{{ info.title }}</h2>
    <p>{{ info.author }}</p>
    <p>{{ info.year }}</p>
  </div>
</template>

<script>
export default {
  name: "Card",
  props: {
    info: Object,
  },
};
</script>

<style lang='scss' scoped>
div {
  padding-bottom: 50px;
}

img {
  width: 80%;
}

h2 {
  text-transform: uppercase;
  margin: 30px 0;
}

p {
  color: #7c786c;
  margin-bottom: 5px;
}
</style>