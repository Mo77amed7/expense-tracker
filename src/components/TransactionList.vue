<template>
  <section>
    <h2>History</h2>
    <hr />
    <ul v-if="transactions.length > 0">
      <li
        v-for="transaction in transactions"
        :key="transaction.title"
        :class="transaction.amount > 0 ? 'plus' : 'minus'"
      >
        <span>{{ transaction.title }}</span>
        <span>{{ transaction.amount }}$</span>
        <button @click="deleteTransaction(transaction.id)">X</button>
      </li>
    </ul>
    <p v-else>No transactions available</p>
  </section>
</template>
<script>
export default {
  name: "TransactionList",
  props: ["transactions"],
  methods: {
    deleteTransaction(id) {
      const transactions =
        JSON.parse(localStorage.getItem("transactions")) || [];
      const updated = transactions.filter((t) => t.id !== id);
      localStorage.setItem("transactions", JSON.stringify(updated));
      this.$emit("transaction-deleted", updated);
    },
  },
};
</script>

<style scoped>
ul {
  list-style: none;
  margin: 0;
  padding: 0;
}
li {
  background-color: white;
  position: relative;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 5px;
  border-right-width: 2px;
  border-right-style: solid;
  box-shadow: 0px 0px 1px 1px #ccc;
  margin: 10px 0px;
}

button {
  position: absolute;
  left: -18px;
  width: 18px;
  height: 18px;
  border: 0;
  color: white;
  background-color: #660a0a;
  cursor: pointer;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 3px;
  opacity: 0;
}
li:hover button {
  opacity: 1;
}
li.plus {
  border-right-color: green;
}
li.minus {
  border-right-color: rgb(204, 4, 4);
}
</style>
