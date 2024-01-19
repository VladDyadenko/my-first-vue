<template>
  <input class="custom-input" v-model.number="price" placeholder="Ціна, від" />
</template>

<script>
export default {
  name: "CostomInput",
  data() {
    return {
      price: "",
    };
  },
};
</script>

<style lang="scss" scoped>
@import "../../assets/scss/variables";

.custom-input {
  min-height: 44px;
  min-width: 220px;
  border: 2px solid $main-color;
  background: #fff;
  font-size: 18px;
  outline: none;
  line-height: inherit;
  padding: 8px 15px;
}
</style>
