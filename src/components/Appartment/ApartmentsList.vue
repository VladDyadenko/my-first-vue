<template>
  <ContainerMain>
    <slot name="title"></slot>
    <ul class="apartments-list">
      <template v-for="apartment in items">
        <slot name="apartment" v-bind:apartment="apartment"></slot
      ></template>
    </ul>
  </ContainerMain>
</template>

<script>
import ContainerMain from "../shared/ContainerMain.vue";
export default {
  name: "ApartmentsList",
  components: {
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
  justify-content: center;
  gap: 30px;
}
</style>
