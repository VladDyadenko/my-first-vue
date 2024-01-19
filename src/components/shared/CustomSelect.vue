<template>
  <div class="select">
    <select
      class="custom-select"
      v-model="selected"
      @click="$emit('click', selected)"
    >
      <option value="" selected>Місто</option>
      <option
        class="custom-option"
        v-for="item in uniqueCity"
        :value="modelValue"
        :key="item"
      >
        {{ item }}
      </option>
    </select>
  </div>
</template>

<script>
export default {
  name: "CustomSelect",
  props: {
    items: {
      type: Array,
      required: true,
    },
    modelValue: {
      type: String,
    },
  },
  data() {
    return {
      selected: "",
    };
  },
  computed: {
    uniqueCity() {
      const uniqueCity = [
        ...new Set(this.items.map((item) => item.location.city)),
      ];
      return uniqueCity.sort();
    },
  },
  watch: {
    selected(newValue) {
      console.log("Selected value changed:", newValue);
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../../assets/scss/variables";

.custom-select {
  min-height: 44px;
  min-width: 220px;
  border: 2px solid $main-color;
  background: #fff;
  font-size: 18px;
  outline: none;
  line-height: inherit;
  padding: 8px 15px;
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;
}
.custom-select::-ms-expand {
  display: none;
}
.custom-option {
  width: 140px;
  color: $main-text-color;
  font-family: Montserrat;
  font-size: 18px;
  font-weight: 400;
  line-height: normal;
}
.select {
  height: 44px;
  width: 220px;
  overflow: hidden;
  position: relative;
}
.select:after {
  content: "▼ ";
  padding: 17px 8px;
  position: absolute;
  right: 0;
  top: 0;
  z-index: 1;
  text-align: center;
  width: 20%;
  height: 100%;
  pointer-events: none;
}
</style>
