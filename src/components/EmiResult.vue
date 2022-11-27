<template>
  <base-card>
    <p>Monthly EMI ---------------- {{ month }}</p>
    <p>Loan Amount ---------------- {{ amount }}</p>
    <p>Interest Payable ----------- {{ rate }}</p>
    <p>Total Payable -------------- {{ total }}</p>
  </base-card>
</template>

<script>
import BaseCard from './BaseCard.vue';
export default {
  components: { BaseCard },
  props: ['amount', 'rate', 'total', 'month'],
};
</script>
