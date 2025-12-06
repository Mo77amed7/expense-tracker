<template>
  <section class="income-exp">
    <div class="income">
      <h2>Income</h2>
      <p>+$0.00</p>
    </div>
    <span class="divider"></span>
    <div class="expense">
      <h2>Expense</h2>
      <p>-$0.00</p>
    </div>
  </section>
</template>
<script>
export default {
  name: "IncomeExpenses",
};
</script>
<style scoped>
.income-exp {
  display: flex;
  background-color: white;
  justify-content: space-around;
  align-items: center;
  height: 100px;
}
.divider {
  width: 2px;
  height: 80%;
  background-color: #ddd;
}
.income,
.expense {
  display: flex;
  align-items: center;
  flex-direction: column;
}
h2 {
  margin: 0;
}
.income p {
  color: green;
}
.expense p {
  color: rgb(177, 0, 0);
}
</style>
