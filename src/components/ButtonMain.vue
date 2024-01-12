<template>
  <button class="btn btn--outlined" v-bind:type="type">
    {{ btnName }}
  </button>
</template>

<script>
export default {
  name: "ButtonMain",
  props: {
    type: {
      type: String,
      default: "button",
    },
    btnName: {
      type: String,
      requered: true,
    },
  },
  data() {
    return {
      message: "Hello, Vue App!",
    };
  },
  methods: {},
};
</script>

<style lang="scss" scoped>
.btn {
  display: inline-block;
  font-size: 18px;
  background: #ff662d;
  color: #fff;
  cursor: pointer;
  min-width: 220px;
  border: 1px solid transparent;
  padding: 8px 15px;
  margin-right: 8px;
  border-radius: 8px;

  &--outlined {
    background: none;
    border: 1px solid #ff662d;
    color: #ff662d;
  }
}
</style>
