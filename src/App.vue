<template>
  <div id="app">
    <header></header>
    <main>
      <expensesList :paymentsList="paymentsList"/>
      <div class="expenses-form">
        <button @click="addFormBtn">{{ addForm }} форму</button>
        <expensesForm v-if="show" @add-expenses="addExpenses"/>
      </div>
    </main>
  </div>
</template>

<script>
import expensesList from '@/components/ExpensesList'
import expensesForm from '@/components/expensesForm'

export default {
  name: 'App',
  components: {
    expensesList,
    expensesForm
  },
  data: () => ({
    paymentsList: [],
    show: false,
    addForm: 'показать'
  }),
  methods: {
    fetchPaymentsData () {
      return [
        {
          date: '28.03.2020',
          category: 'Food',
          value: 1488
        },
        {
          date: '14.88.2002',
          category: 'Food',
          value: 1231
        },
        {
          date: '32.22.2800',
          category: 'Food',
          value: 2033
        }
      ]
    },
    addExpenses (data) {
      this.paymentsList.push(data)
    },
    addFormBtn () {
      this.show = !this.show
      !this.show ? this.addForm = 'показать' : this.addForm = 'скрыть'
    }
  },
  created () {
    setTimeout(() => {
      this.paymentsList = this.fetchPaymentsData()
    }, 500)
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
main{
  display: flex;
  justify-content: center;
}
button {
  background-color: #32AB9B;
  border: 0;
  width: 100px;
  height: 40px;
  border-radius: 5px;
}
.expenses-form{
  width: 250px;
}
</style>
