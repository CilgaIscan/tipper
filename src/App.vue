<template>
  <div id="app">
    <span>
      <p>Please enter your voucher amount: 
      <input type="number" v-model.number="voucher" @change="onChange" /> </p>
    </span>
    <span>
      <p>Please select desired tip percentage:
      <select v-model="tipPercentage" @change="onChange">
        <option
          :value="percent"
          :key="percent"
          v-for="percent in percentages"
        >
          {{ percent }}
        </option>
      </select> </p>
    </span>
    <span>
      <p> You should be tipping {{ result }} TL. </p>
    </span>
  </div>
</template>

<script>
export default {
  name: 'App',
  data: function () {
      return {
        voucher: 45,
        percentages: [5, 10, 15, 20],
        tipPercentage: 10,
        result: null,
      };
  },
  methods: {
    onChange() {
      switch (this.tipPercentage) {
        case 5:
          this.result = this.voucher * 0.05;
          break;
        case 10:
          this.result = this.voucher * 0.1;
          break;
        case 15:
          this.result = this.voucher * 0.15;
          break;
        case 20:
          this.result = this.voucher * 0.2;
          break;
        default:
          console.log("Percent is not found!");
      }
    },
  },
};
</script>

<style>

</style>
