<template>
  <div class="b-outer">
    <div class="b-numbers">
      <div
        v-for="n in numberZone"
        :key="n"
        :data-button="n"
        class="b-button button-number"
        @click="buttonClick"
      >
        {{ n }}
      </div>
    </div>
    <div class="b-chars">
      <div
        v-for="c in charZone"
        :key="c"
        :data-button="c"
        class="b-button"
        @click="buttonClick"
      >
        {{ c }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Buttons',
  data() {
    return {
      numberZone: [...[...Array(9).keys()].map((i) => i + 1), '.', 0, '+/-'],
      charZone: [
        ...[...Array(26).keys()].map((i) => String.fromCharCode(i + 65)),
        'SP',
        'DEL',
        '/',
        'CLR',
      ],
    };
  },
  methods: {
    buttonClick(e) {
      let button = e.currentTarget.dataset.button;
      this.$emit('buttonClick', button);
    },
  },
};
</script>

<style scoped lang="scss">
.b-outer {
  display: flex;
  align-items: flex-end;
  gap: 12px;
}
.b-numbers {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  column-gap: 12px;
  row-gap: 12px;
}
.b-chars {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  column-gap: 12px;
  row-gap: 12px;
}
.b-button {
  cursor: pointer;
  width: 48px;
  height: 48px;
  background-color: #222222;
  color: #ffffff;
  font-size: 20px;
  display: flex;
  justify-content: center;
  align-items: center;
}
.button-number {
  border-radius: 50%;
}
@media (max-width: 500px) {
  .b-outer {
    flex-direction: column-reverse;
    align-items: center;
  }
}
</style>
