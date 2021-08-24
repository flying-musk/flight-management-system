<template>
  <div>
    <h1>Flight Management System</h1>
    <div class="f-outer">
      <div class="f-main">
        <Display :display="display" />
        <Buttons @buttonClick="buttonClick" />
      </div>
    </div>
  </div>
</template>

<script>
import Display from './Display.vue';
import Buttons from './Buttons.vue';
export default {
  name: 'flight-management-system',
  components: {
    Display,
    Buttons,
  },
  data() {
    return {
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
  padding: 16px;
  display: flex;
  flex-direction: column;
  gap: 16px;
}
</style>
