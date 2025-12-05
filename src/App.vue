<template>
  <div class="expense-tracker">
    <the-header></the-header>
    <the-balance></the-balance>
    <income-expenses></income-expenses>
    <add-transaction></add-transaction>
    <transaction-list></transaction-list>
  </div>
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

<style scoped>
.expense-tracker {
  background-color: #eee;
  width: 50%;
  margin: 20px auto;
  box-shadow: 1px 1px 1px 1px rgb(225, 222, 222),
    1px 1px 1px 1px rgb(225, 222, 222);
  padding: 20px;
}
</style>
