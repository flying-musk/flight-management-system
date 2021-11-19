<template>
  <div class="d-outer">
    <span class="d-start">&gt;&nbsp;</span>
    <input class="d-input" type="text" :value="display" disabled ref="input" />
  </div>
</template>

<script>
export default {
  name: 'Display',
  props: ['display'],
  watch: {
    display: {
      immediate: true,
      handler() {
        this.$nextTick(function () {
          this.$refs.input.scrollLeft =
            this.$refs.input.scrollWidth - this.$refs.input.clientWidth;
        });
      },
    },
  },
};
</script>

<style scoped lang="scss">
.d-outer {
  background-color: #222222;
  color: #ffffff;
  padding: 16px;
  font-family: Consolas, monaco, monospace;
  display: flex;
  align-items: center;
}
.d-start {
  color: #36f036;
}
.d-input {
  width: 0;
  flex-grow: 1;
  border: none;
  background-color: #222222;
  color: #ffffff;
  padding: 0px;
  font-family: Consolas, monaco, monospace;
  font-size: 20px;
}
.d-input:focus {
  outline: none;
}
</style>
