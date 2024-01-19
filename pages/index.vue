<template>
  <main class="main">
    <Waiter />
    <TipSection v-model="tipAmount" />
    <Rate />
    <Pay :tipAmount="tipAmount" />
  </main>
</template>

<script>
export default {
  head() {
    return {
      title: "Tip payment"
    };
  },
  data() {
    return {
      tipAmount: '5€',
    };
  },
}
</script>

<style lang="scss" scoped>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@500;600&display=swap');

.main {
  background-color: $bg-color;
  border-radius: 30px;
  padding: 54px 10px 35px;
}

.waiter {
  &-img {
    width: 355px;
    height: 400px;
  }
}
</style>
