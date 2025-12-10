<template>
  <section>
    <h2>Add New Transaction</h2>
    <hr />
    <form @submit.prevent="submit">
      <div>
        <label for="text">Text</label>
        <input
          id="text"
          type="text"
          placeholder="Enter text.."
          v-model.trim="title"
        />
      </div>
      <div>
        <label for="amount">Amount<br></br>(negative-expense-positive-income)</label>
        <input
          id="amount"
          type="number"
          placeholder="Enter amount..."
          v-model.number="amount"
        />
      </div>
      <p class="error" v-if="error">
        {{ error }}
      </p>
      <div class="action">
        <button type="submit">Add Transaction</button>
      </div>
    </form>
  </section>
</template>
<script>
import {useToast} from"vue-toastification";
export default {
  name: "AddTransaction",
  data() {
    return {
        title : "",
        amount: null,
        error: "",
      }
    },
  methods: {
    submit() {
      if (!this.title) {
        this.error = "Please enter a valid title";
        return;
      }
      if (!this.amount) {
        this.error = "Please enter a valid amount";
        return;
      }

      this.error = "";
      const toast = useToast();
      toast.success("Transaction added successfully!");

      this.$emit("add-transaction", {
        id: Date.now(),
        title: this.title,
        amount: this.amount,
      });

      this.title = "";
      this.amount = null;
    }
  }
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
  box-shadow: 0px 0px 1px 1px #ccc;
  font-size: 16px;
  margin-top: 5px;
}
input:focus {
  outline: none;
  box-shadow: 0px 0px 2px 2px #888888;
}
input::placeholder {
  color: #ccc;
}
.action {
  display: flex;
  justify-content: center;
  align-items: center;
}
.error {
  color: red;
  margin: 5px 0;
}
button {
  width: 50%;
  margin-top: 20px;

  padding: 10px;
  border: 0;
  background-color: #333;
  color: white;
  font-size: 16px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}
button:hover {
  background-color: #555;
}
</style>
