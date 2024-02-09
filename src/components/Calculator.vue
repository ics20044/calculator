<template>
  <div class="calculator">
    <input type="text" class="display" :value="display" disabled />
    <div class="keys">
      <button class="operator clear" @click="clearDisplay()">C</button>
      <button class="operator" @click="appendToDisplay('/')">÷</button>
      <button class="operator" @click="appendToDisplay('*')">x</button>
      <button class="operator" @click="appendToDisplay('-')">-</button>
      <button class="operator" @click="appendToDisplay('+')">+</button>
      <button @click="appendToDisplay('7')">7</button>
      <button @click="appendToDisplay('8')">8</button>
      <button @click="appendToDisplay('9')">9</button>
      <button @click="appendToDisplay('4')">4</button>
      <button @click="appendToDisplay('5')">5</button>
      <button @click="appendToDisplay('6')">6</button>
      <button @click="appendToDisplay('1')">1</button>
      <button @click="appendToDisplay('2')">2</button>
      <button @click="appendToDisplay('3')">3</button>
      <button @click="appendToDisplay('0')">0</button>
      <button class="decimal" @click="appendToDisplay('.')">.</button>
      <button class="equal" @click="calculateResult()">=</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      display: "",
    };
  },
  methods: {
    clearDisplay() {
      this.display = "";
    },
    appendToDisplay(v) {
      this.display = this.display + v;
      console.log(this.display);
    },
    calculateResult() {
      try {
        this.display = eval(this.display);
      } catch (error) {
        this.display = "Error";
      }
    },
  },
};
</script>

<style scoped>
.calculator {
  width: 300px;
  margin: 100px auto;
  border-radius: 10px;
  overflow: hidden;
  box-shadow: 0px 0px 20px rgba(0, 0, 0, 0.1);
  background-color: #f8f8f8;
  font-family: "Roboto", sans-serif;
}

.display {
  width: calc(100% - 20px);
  margin: 10px;
  padding: 10px;
  font-size: 2em;
  text-align: right;
  border: none;
  outline: none;
  background-color: transparent;
}

.keys {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-gap: 5px;
  padding: 10px;
}

button {
  padding: 20px;
  font-size: 1.2em;
  border: none;
  outline: none;
  cursor: pointer;
  background-color: #fff;
  transition: background-color 0.3s ease;
  border-radius: 5px;
  box-shadow: 0px 3px 6px rgba(0, 0, 0, 0.1);
  color: #333;
}

button:hover {
  background-color: #f0f0f0;
}

.operator,
.equal {
  background-color: #0953b5;
  color: #fff;
  box-shadow: 0px 3px 6px rgba(0, 245, 167, 0.377);
}

.operator:hover,
.equal:hover {
  background-color: #82e600;
}

.clear {
  background-color: #c3c008;
}

.clear:hover {
  background-color: #2b84c0;
}

.decimal {
  background-color: #35585f;
}

.decimal:hover {
  background-color: #2980b9;
}
</style>
