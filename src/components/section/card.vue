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
img {
  width: 100%;
}
</style>