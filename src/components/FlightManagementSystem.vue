<template>
  <div>
    <h1>Flight Management System</h1>
    <div class="f-outer">
      <div class="f-main">
        <Random :newRandomStringFlag="newRandomStringFlag" />
        <Display :display="display" />
        <Buttons @buttonClick="buttonClick" />
      </div>
    </div>
  </div>
</template>

<script>
import Random from './Random.vue';
import Display from './Display.vue';
import Buttons from './Buttons.vue';
export default {
  name: 'flight-management-system',
  components: {
    Random,
    Display,
    Buttons,
  },
  data() {
    return {
      newRandomStringFlag: 0,
      display: '',
      signState: '',
    };
  },
  watch: {
    signState(newValue, oldValue) {
      if (newValue === '') {
        return;
      }
      if (oldValue !== '') {
        this.display = this.display.substring(0, this.display.length - 1);
      }
      this.display += newValue;
    },
  },
  methods: {
    buttonClick(button) {
      if (button === '+/-') {
        this.signState = this.signState === '+' ? '-' : '+';
      } else {
        this.signState = '';
        if (button === 'SP') {
          this.display += ' ';
        } else if (button === 'DEL') {
          this.display = this.display.substring(0, this.display.length - 1);
        } else if (button === 'CLR') {
          this.display = '';
          this.newRandomStringFlag += 1;
        } else {
          this.display += button;
        }
      }
    },
  },
};
</script>

<style scoped lang="scss">
.f-outer {
  min-height: 64vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
.f-main {
  background-color: #d8c6ae;
  max-width: 560px;
  padding: 12px;
  display: flex;
  flex-direction: column;
  gap: 12px;
}
</style>
