<template>
  <div>
    <h1>Flight Management System</h1>
    <div class="f-main">
      <Display :display="display" />
      <Buttons />
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
};
</script>

<style scoped lang="scss">
.f-main {
  background-color: #d8c6ae;
  max-width: 560px;
  padding: 8px;
  display: flex;
  flex-direction: column;
  gap: 8px;
}
</style>
