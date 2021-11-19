<template>
  <div class="r-outer">{{ randomString }}</div>
</template>

<script>
export default {
  name: 'random',
  props: ['newRandomStringFlag'],
  data() {
    return {
      charSet: [
        ...[...Array(26).keys()].map((i) => String.fromCharCode(i + 65)),
      ],
      randomString: '',
    };
  },
  watch: {
    newRandomStringFlag: {
      immediate: true,
      handler() {
        this.randomString = this.charSet
          .sort(() => Math.random() - 0.5)
          .slice(0, 6)
          .join('');
      },
    },
  },
};
</script>

<style lang="scss" scoped>
.r-outer {
  background-color: #cccccc;
  padding: 16px;
  font-family: Consolas, monaco, monospace;
  font-size: 20px;
}
</style>
