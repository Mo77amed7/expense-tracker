<template>
  <section>
    <h2>Your Balance</h2>
    <p>{{ balance }}$</p>
  </section>
</template>

<script>
export default {
  name: "TheBalance",
  props: ["balance"],
};
</script>
<style scoped>
h2 {
  margin-bottom: 0px;
}
p {
  margin-top: 5px;
}
</style>
