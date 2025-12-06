<template>
  <section>
    <h2>History</h2>
    <hr>
    <ul>
      <li class="plus">
        <span>Sneakers</span>
        <span>200$</span>
        <button>X</button>
      </li>
    </ul>
  </section>
</template>
<script>
export default {
  name: "TransactionList",
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
