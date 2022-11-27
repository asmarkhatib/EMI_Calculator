<template>
  <div>
    <base-card>
      <div>
        <label for="amount">Loan Amount: </label>
        <input
          type="tel"
          name="amount"
          id="amount"
          v-model.number="loanInput"
        />
      </div>
      <div>
        <label for="rate">Interest: </label>
        <input
          type="tel"
          name="rate"
          id="rate"
          v-model.number="interestInput"
        />
      </div>
      <div>
        <label for="year">Years: </label>
        <input type="tel" name="year" id="year" v-model.number="yearInput" />
      </div>
      <div>
        <button @click="submitInputs">Submit</button>
      </div>
    </base-card>
  </div>
</template>

<script>
export default {
  emits: ['submit-data'],
  data() {
    return {
      loanInput: null,
      interestInput: null,
      yearInput: null,
    };
  },
  methods: {
    submitInputs() {
      // Using Math property //
      // const months = this.yearInput * 12;

      // const interestPerMonth = this.interestInput / 100 / 12;

      // const x = Math.pow(1 + interestPerMonth, months);
      // const monthlyInstallment =
      //   (this.loanInput * x * interestPerMonth) / (x - 1);

      // const total = monthlyInstallment * months;

      // const interestToPay = total - this.loanInput;
      let interestToPay = 0;
      const amount = this.loanInput;

      const interestPerMonth = this.interestInput / 12;
      const results = [];

      for (let i = 1; i <= this.yearInput * 12; i++) {
        const result = (interestPerMonth / 100) * amount;
        results.push(result);
      }
      console.log('results =>', results);

      results.forEach((ele) => (interestToPay += ele));
      console.log(interestToPay);
      const total = interestToPay + this.loanInput;
      const monthlyInstallment = total / (this.yearInput * 12);
      this.$emit(
        'submit-data',
        this.loanInput,
        interestToPay,
        monthlyInstallment,
        total
      );

      (this.loanInput = null),
        (this.interestInput = null),
        (this.yearInput = null);
    },
  },
};
</script>

<style scoped>
div {
  display: grid;
}
</style>
