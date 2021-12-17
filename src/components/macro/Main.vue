<template>
  <main>
    <Select @scelta="filtraGenere" />

    <div class="container">
      <div v-for="(album, index) in albums" :key="index" class="song">
        <Card :info="album" />
      </div>
    </div>
  </main>
</template>

<script>
import axios from "axios";
import Card from "../section/card.vue";
import Select from "../section/Select.vue";

export default {
  name: "Main",
  components: {
    Card,
    Select,
  },
  data() {
    return {
      albums: null,
      sceltaGenere: "",
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
  methods: {
    filtraGenere(payload) {
      this.sceltaGenere = payload;
    },
  },
  computed: {
    genereFiltered() {
      const arrayFiltered = this.albums.filter((elm) => {
        return elm.genre.includes(this.sceltaGenere);
      });

      return arrayFiltered;
    },
  },
};
</script>

<style lang="scss" scoped>
main {
  background-color: #1e2d3b;
  height: calc(100vh - 65px);
  overflow: scroll;
  overflow-x: hidden;
}

.container {
  max-width: 1072px;
  margin: 0 auto;
  display: flex;
  flex-wrap: wrap;
  padding-top: 30px;
  justify-content: space-between;

  .song {
    padding-top: 20px;
    text-align: center;
    width: calc((100% / 5) - 10px);
    background-color: #2e3a46;
    color: white;
    margin: 20px 0;
  }
}
</style>