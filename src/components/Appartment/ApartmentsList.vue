<template>
  <ContainerMain>
    <ul class="apartments-list">
      <ApartmentsItem
        v-for="{ descr, rating, price, imgUrl, id } in items"
        :key="id"
        :descr="descr"
        :rating="rating"
        :price="price"
        :imgSrc="imgUrl"
        class="apartments-list__item"
      />
    </ul>
  </ContainerMain>
</template>

<script>
import ApartmentsItem from "./AppartmentsItem.vue";
import ContainerMain from "../shared/ContainerMain.vue";
export default {
  name: "ApartmentsList",
  components: {
    ApartmentsItem,
    ContainerMain,
  },
  props: {
    items: {
      type: Array,
      default: () => [],
    },
  },
};
</script>

<style lang="scss" scoped>
.apartments-list {
  display: flex;
  flex-wrap: wrap;
  margin-left: -15px;
  margin-right: -15px;

  &__item {
    margin-bottom: 30px;
  }
}
</style>
