<template>
  <div>
<!--    <div class="test">{{ paymentsList }}</div>-->
    <div v-if="paymentsList" class="payments-list">
      <div class="payment">
        <div class="payment__row">#</div>
        <div class="payment__row">Date</div>
        <div class="payment__row">Category</div>
        <div class="payment__row">Value</div>
      </div>
      <div class="payment"
      v-for="(payment, i_payment) in paymentsList" :key="i_payment"
      >
        <div class="payment__row">{{i_payment + 1}}</div>
        <div class="payment__row">{{payment.date }}</div>
        <div class="payment__row">{{payment.category }}</div>
        <div class="payment__row">{{payment.value }}</div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ExpensesList',
  props: {
    paymentsList: {
      type: Array,
      required: true
    }
  }
}
</script>

<style scoped lang="scss">
.payments-list{
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.payment{
  width: 550px;
  border-bottom: 1px solid #F5F5F5;
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 20px;
  padding: 10px 0 10px 0;
  &__row{
    width: 100px;
  }
  &__row:first-child{
    width: 0px;
  }
}
.payment:last-child{
  border-bottom: 0px;
}
</style>
