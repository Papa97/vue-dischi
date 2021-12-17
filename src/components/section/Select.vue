<template>
  <div class="select">
    <span>Scegli per genere da filtrare </span>
    <select
      name="select-genre"
      v-model="sceltaGenere"
      @change="$emit('scelta', sceltaGenere)"
    >
      <option value="Rock">Rock</option>
      <option value="Pop">Pop</option>
      <option value="Jazz">Jazz</option>
      <option value="Metal">Metal</option>
    </select>
  </div>
</template>

<script>
export default {
  name: "Select",
  data() {
    return {
      sceltaGenere: "",
    };
  },
};
</script>

<style lang="scss" scoped>
* {
  text-align: center;
  margin-top: 20px;
}
span {
  color: white;
}
</style>