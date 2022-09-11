<script setup>
import { reactive } from "vue";

import CreditCard from "./components/CreditCard.vue";
import CardBack from "./components/CardBack.vue";

const handleSubmit = (e) => {
  e.preventDefault();
  console.log(e);
};
const card = reactive({
  name: "",
  cardNumber: "",
  exp: {
    mm: "",
    yy: "",
  },
  cvc: "",
});
</script>

<template>
  <main>
    <credit-card :card="card"></credit-card>
    <card-back></card-back>
    <img src="/images/bg-main-desktop.png" alt="Bg" class="bg-img" />
    <div class="spacer"></div>
    <div class="container">
      <form v-on:submit="handleSubmit">
        <label for="">Cardholder name</label>
        <input
          type="text"
          class="full-width"
          placeholder="e.g. Jane Appleseed"
          style="margin-bottom: 20px"
          v-model="card.name"
        />
        <label for="">Card number</label>
        <input
          type="text"
          class="full-width"
          placeholder="e.g. 1234 5678 9123 0000"
          style="margin-bottom: 20px"
          v-model="card.cardNumber"
        />
        <div class="flex" style="margin-bottom: 20px">
          <div style="margin-right: 20px">
            <label for="">exp. date (mm/yy)</label>
            <div class="flex">
              <input
                type="number"
                placeholder="MM"
                class="inline"
                style="margin-right: 10px"
                v-model="card.exp.mm"
              />
              <input
                type="number"
                placeholder="YY"
                class="inline"
                v-model="card.exp.yy"
              />
            </div>
          </div>
          <div>
            <label for="">cvc</label>
            <input type="number" placeholder="e.g. 123" v-model="card.cvc" />
          </div>
        </div>
        <button type="submit">Confirm</button>
      </form>
    </div>
  </main>
</template>

<style>
main {
  display: flex;
}

.bg-img {
  height: 100vh;
  background-size: cover;
}

label {
  text-transform: uppercase;
}

.full-width {
  width: 100%;
}

input {
  width: 100px;
  padding: 8px 10px;
  margin: 8px 0;
  box-sizing: border-box;
  border: 1px solid var(--light-grayish-violet);
  border-radius: 3px;
}

input:focus {
  border: 1px solid var(--dark-grayish-violet);
}

.error {
  border: 1px solid red;
}

.container {
  display: flex;
  padding: 20px;
  width: 200px;
  max-width: 200px;
  justify-content: flex-end;
  align-items: center;
  margin-right: 200px;
}

input::-webkit-outer-spin-button,
input::-webkit-inner-spin-button {
  -webkit-appearance: none;
  margin: 0;
}

input[type="number"] {
  -moz-appearance: textfield;
}

.spacer {
  flex-grow: 1;
}

.flex {
  display: flex;
}

button {
  display: block;
  color: var(--white);
  background-color: var(--very-dark-violet);
  border-radius: 5px;
  padding: 10px 20px;
  width: 100%;
  margin-top: 20px;
}

.front-card {
  position: absolute;
  left: 200px;
  top: 100px;
  z-index: 1;
  height: 150px;
  box-shadow: 0px 6px 12px 4px #0000007a;
  border-radius: 6px;
}

.back-card {
  position: absolute;
  left: 250px;
  top: 300px;
  z-index: 1;
  height: 150px;
  box-shadow: 0px 6px 12px 4px #0000007a;
  border-radius: 6px;
}
</style>
