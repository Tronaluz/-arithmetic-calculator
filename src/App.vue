<template>
  <div class="container-fluid p-3 bg-light">
    <input v-model.number="num1" type="number" placeholder="Número 1">
    <select v-model="operation">
      <option value="+">+</option>
      <option value="-">-</option>
      <option value="*">*</option>
      <option value="/">/</option>
    </select>
    <input v-model.number="num2" type="number" placeholder="Número 2">
    <button @click="calculate">Calcular</button>
    <p>{{ result }}</p>
  </div>
</template>

<script>
export default {
  data() {
    return {
      num1: '',
      num2: '',
      operation: '+',
      result: ''
    }
  },
  methods: {
    calculate() {
      const num1 = parseFloat(this.num1)
      const num2 = parseFloat(this.num2)
      
      switch(this.operation) {
        case '+':
          this.result = num1 + num2
          break
        case '-':
          this.result = num1 - num2
          break
        case '*':
          this.result = num1 * num2
          break
        case '/':
          if(num2 !== 0) {
            this.result = num1 / num2
          } else {
            this.result = 'Divisão por zero!'
          }
          break
      }
    }
  }
}
</script>

<style scoped>
.container {
  max-width: 300px;
  margin: 0 auto;
}

input, select, button {
  margin: 10px;
  padding: 10px;
  font-size: 18px;
}

button {
  background-color: #4CAF50;
  color: white;
  border: none;
  cursor: pointer;
}

button:hover {
  background-color: #45a049;
}
</style>
