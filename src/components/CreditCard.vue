<template>
  <div class="img">
    <div class="flex">
      <div class="circle"></div>
      <div class="circle bordered"></div>
    </div>
    <div class="spacer"></div>
    <br />
    <p class="card-number">
      {{ prettierCardNumber }}
    </p>
    <br />
    <div class="flex">
      {{ defaultName }}
      <div class="spacer"></div>
      {{ defaultDate }}
    </div>
  </div>
</template>

<script>
export default {
  props: ["card"],
  computed: {
    prettierCardNumber() {
      if (!this.card.cardNumber) {
        return "0000 0000 0000 0000";
      } else {
        return Array(...this.card.cardNumber)
          .map((item, index) => ((index + 1) % 4 == 0 ? item + " " : item))
          .join("");
      }
    },
    defaultDate() {
      let formatedDate = "";
      if (this.card.exp.mm) formatedDate += this.card.exp.mm;
      else formatedDate += "00";
      formatedDate += " / ";
      if (this.card.exp.yy) formatedDate += this.card.exp.yy;
      else formatedDate += "00";
      return formatedDate;
    },
    defaultName() {
      return this.card.name ? this.card.name : "Your Name.";
    },
  },
};
</script>

<style scoped>
.flex {
  display: flex;
}

.card-number {
  font-size: 22px;
  padding: 5px;
}
.circle {
  border-radius: 50%;
  height: 25px;
  width: 25px;
  background-color: white;
  display: inline-block;
  margin: 5px;
}
.circle.bordered {
  background-color: transparent;
  outline: 1px solid white;
}
.img {
  box-shadow: 1px 2px 14px 4px #00000061;
  border-radius: 6px;
  padding: 10px;
  color: var(--white);
  position: absolute;
  z-index: 1;
  left: 200px;
  top: 130px;
  display: flex;
  flex-direction: column;
  height: 150px;
  width: 273.672px;
  background-image: url("/images/bg-card-front.png");
  background-size: cover;
  background-repeat: no-repeat;
}
</style>