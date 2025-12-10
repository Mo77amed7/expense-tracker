<template>
  <the-header></the-header>
  <the-balance
    @transaction-added="updateTransactions"
    :balance="balance"
  ></the-balance>
  <income-expenses :income="income" :expense="expense"></income-expenses>
  <transaction-list
    :transactions="transactions"
    @transaction-deleted="deleteTransactions"
  ></transaction-list>
  <add-transaction @transaction-added="updateTransactions"></add-transaction>
</template>

<script>
import AddTransaction from "./components/AddTransaction.vue";
import IncomeExpenses from "./components/IncomeExpenses.vue";
import TransactionList from "./components/TransactionList.vue";
import TheHeader from "./components/TheHeader.vue";
import TheBalance from "./components/TheBalance.vue";
export default {
  name: "The-App",
  emits: ["transaction-updated"],
  data() {
    return {
      balance: 0,
      income: 0,
      expense: 0,
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
  methods: {
    updateTransactions(newTransaction) {
      if (newTransaction.amount > 0) {
        this.income += newTransaction.amount;
      } else {
        this.expense += newTransaction.amount;
      }
      this.balance = this.income + this.expense;
      this.transactions.push(newTransaction);
      localStorage.setItem("transactions", JSON.stringify(this.transactions));
    },
    deleteTransactions(updatedTransactions) {
      this.income = 0;
      this.expense = 0;
      updatedTransactions.forEach((transaction) => {
        if (transaction.amount > 0) {
          this.income += transaction.amount;
        } else {
          this.expense += transaction.amount;
        }
      });
      this.balance = this.income + this.expense;
      this.transactions = updatedTransactions;
    },
  },
  created() {
    const transactions = JSON.parse(localStorage.getItem("transactions")) || [];
    transactions.forEach((transaction) => {
      if (transaction.amount > 0) {
        this.income += transaction.amount;
      } else {
        this.expense += transaction.amount;
      }
    });
    this.balance = this.income + this.expense;
    this.transactions = transactions;
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
section:not(:last-child) {
  margin-bottom: 40px;
}
</style>
