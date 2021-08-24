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
    };
  },
  methods: {
    buttonClick(button) {
      this.display += button;
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
