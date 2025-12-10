<template>
  <the-header></the-header>
  <the-balance :balance="balance"></the-balance>
  <income-expenses :income="income" :expense="expense"></income-expenses>
  <transaction-list
    :transactions="transactions"
    @delete-transaction="handleDelete"
  ></transaction-list>
  <add-transaction @add-transaction="handleAdd"></add-transaction>
</template>

<script>
import AddTransaction from "./components/AddTransaction.vue";
import IncomeExpenses from "./components/IncomeExpenses.vue";
import TransactionList from "./components/TransactionList.vue";
import TheHeader from "./components/TheHeader.vue";
import TheBalance from "./components/TheBalance.vue";
export default {
  name: "The-App",
  data() {
    return {
      transactions: [],
    };
  },
  components: {
    TheHeader,
    TheBalance,
    IncomeExpenses,
    AddTransaction,
    TransactionList,
  },
  computed: {
    income() {
      return this.transactions
        .filter((t) => t.amount > 0)
        .reduce((acc, t) => acc + t.amount, 0);
    },
    expense() {
      return this.transactions
        .filter((t) => t.amount < 0)
        .reduce((acc, t) => acc + t.amount, 0);
    },

    balance() {
      return this.income + this.expense;
    },
  },
  methods: {
    handleAdd(transaction) {
      this.transactions.push(transaction);
      localStorage.setItem("transactions", JSON.stringify(this.transactions));
    },
    handleDelete(id) {
      this.transactions = this.transactions.filter((t) => t.id !== id);
      localStorage.setItem("transactions", JSON.stringify(this.transactions));
    },
  },
  created() {
    const data = JSON.parse(localStorage.getItem("transactions")) || [];
    this.transactions = data;
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Comic+Neue:ital,wght@0,300;0,400;0,700;1,300;1,400;1,700&display=swap");
body {
  margin: 0px;
  padding: 0px;
}
* {
  box-sizing: border-box;
}
#app {
  background-color: #eee;
  width: 50%;
  margin: 20px auto;
  box-shadow: 0px 0px 10px 0px #aaa, 0px 0px 20px 0px #ccc;
  padding: 20px;
  font-family: "Comic Neue", cursive;
}
@media (max-width: 767px) {
  #app {
    width: 90%;
    margin: 20px auto;
  }
}
section:not(:last-child) {
  margin-bottom: 40px;
}
</style>
