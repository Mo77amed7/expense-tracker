<template>
  <section>
    <h2>Add New Transaction</h2>
    <hr />
    <form>
      <div>
        <label for="text">Text</label>
        <input id="text" type="text" placeholder="Enter text.." />
      </div>
      <div>
        <label for="amount">Amount(negative-expense-positive-income)</label>
        <input id="amount" type="number" placeholder="Enter amount..." />
      </div>
    </form>
  </section>
</template>
<script>
export default {
  name: "AddTransaction",
};
</script>

<style scoped>
label {
  display: block;
  font-weight: bold;
}
div:first-child {
  margin-bottom: 10px;
}
input {
  padding: 5px;
  border: 0;
  width: 100%;
}
</style>
