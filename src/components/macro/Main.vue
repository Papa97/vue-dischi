<template>
  <main>
    <div class="container">
      <div v-for="(album, index) in albums" :key="index">
        <Card :info="album" />
      </div>
    </div>
  </main>
</template>

<script>
import axios from "axios";
import Card from "../section/card.vue";
export default {
  name: "Main",
  components: {
    Card,
  },
  data() {
    return {
      albums: null,
    };
  },
  created() {
    axios
      .get("https://flynn.boolean.careers/exercises/api/array/music")
      .then((response) => {
        // handle success
        this.albums = response.data.response;
      })
      .catch(function (error) {
        // handle error
        console.log(error);
      });
  },
};
</script>

<style lang="scss" scoped>
main {
  background-color: #1e2d3b;
  height: calc(100vh - 65px);
}

.container {
  background-color: red;
  max-width: 1072px;
  margin: 0 auto;
  display: flex;
  flex-wrap: wrap;
  padding-top: 30px;
  justify-content: space-between;

  div {
    padding-top: 20px;
    text-align: center;
    width: calc((100% / 5) - 10px);
    background-color: cornflowerblue;
    color: white;

    h2 {
      text-transform: uppercase;
      margin-top: 10px;
    }
  }
}
</style>