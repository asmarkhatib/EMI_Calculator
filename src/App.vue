<template>
  <emi-input @submit-data="submitData"></emi-input>
  
    <emi-result
      v-if="isVisible"
      :amount="isAmount"
      :rate="interestPayable"
      :total="total"
      :month="monthlyPayable"
    ></emi-result>
  
</template>

<script>
import EmiInput from './components/EmiInput.vue';
import EmiResult from './components/EmiResult.vue';

export default {
  components: {
    EmiInput,
    EmiResult,
  },
  data() {
    return {
      isAmount: null,
      interestPayable: null,
      total: null,
      isVisible: false,
      monthlyPayable: null,
    };
  },
  provide() {
    return {
      results: this.results,
    };
  },
  methods: {
    submitData(amount, rate, month, total) {
      this.isVisible = true;
      this.isAmount = amount;
      this.interestPayable = rate;
      this.monthlyPayable = month;
      this.total = total;
    },
  },
};
</script>
