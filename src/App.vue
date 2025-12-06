<template>
  <the-header></the-header>
  <the-balance></the-balance>
  <income-expenses></income-expenses>
  <transaction-list></transaction-list>
  <add-transaction></add-transaction>
</template>

<script>
import AddTransaction from "./components/AddTransaction.vue";
import IncomeExpenses from "./components/IncomeExpenses.vue";
import TransactionList from "./components/TransactionList.vue";
import TheHeader from "./components/TheHeader.vue";
import TheBalance from "./components/TheBalance.vue";
export default {
  components: {
    TheHeader,
    TheBalance,
    IncomeExpenses,
    AddTransaction,
    TransactionList,
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
  box-shadow: 1px 1px 1px 1px rgb(225, 222, 222),
    1px 1px 1px 1px rgb(225, 222, 222);
  padding: 20px;
  font-family: "Comic Neue", cursive;
}
section:not(:last-child) {
  margin-bottom: 40px;
}
</style>
