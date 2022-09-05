<template>
  <div class="form">
    <input placeholder="value" v-model="value">
    <input placeholder="category" v-model="category">
    <input placeholder="date" v-model="date">
    <button @click="addExpenses">Add</button>
  </div>
</template>

<script>
export default {
  name: 'expensesForm',
  data: () => ({
    value: '',
    category: '',
    date: ''
  }),
  methods: {
    addExpenses () {
      const { value, category, date } = this
      const data = {
        value,
        category,
        // date: this.date ? this.date : this.currentDay
        date: date || this.currentDay
      }
      this.$emit('add-expenses', data)
    }
  },
  computed: {
    currentDay () {
      const currentDate = new Date()
      const day = currentDate.getDate()
      const month = currentDate.getMonth() + 1
      const year = currentDate.getFullYear()
      return `${day}.${month}.${year}`
    }
  }
}
</script>

<style scoped lang="scss">
.form{
  margin: 20px 0 0 0;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  gap: 20px;
}
input{
  width: 200px;
  height: 40px;
  border: 0px;
  box-shadow: 4px 4px 50px 0px rgba(36, 132, 206, 0.2);
  border-radius: 10px;
  text-align: center;
  outline: none;
}
button{
  background-color: #32AB9B;
  border: 0;
  width: 100px;
  height: 40px;
  border-radius: 5px;
  margin-left: 94px;
}
</style>
