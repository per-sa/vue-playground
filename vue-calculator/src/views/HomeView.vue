<template>
  <div
    class="p-3"
    style="max-width: 400px; margin: 50px auto; background: #234"
  >
    <div
      class="w-full rounded m-1 p-3 text-end lead font-weight-bold text-white bg-vue-dark"
    >
      {{ calculatorValue || 0 }}
    </div>

    <div class="row g-0">
      <div class="col-3" v-for="i in calculatorElements" :key="i">
        <div
          class="lead text-white text-center m-1 py-3 bg-vue-dark rounded hover-class"
          :class="{
            'bg-vue-green': ['C', '*', '/', '-', '+', '%', '='].includes(i),
          }"
          @click="action(i)"
        >
          {{ i }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: "HomeView",
  data() {
    return {
      calculatorValue: "",
      calculatorElements: [
        "C",
        "*",
        "/",
        "-",
        7,
        8,
        9,
        "+",
        4,
        5,
        6,
        "%",
        1,
        2,
        3,
        "=",
        0,
        ".",
      ],
      operator: null,
      previousCalculatorValue: "",
    };
  },
  methods: {
    action(i) {
      if (!isNaN(i) || i === ".") {
        this.calculatorValue += i + "";
      }

      if (i === "C") {
        this.calculatorValue = "";
      }

      if (i === "%") {
        this.calculatorValue = this.calculatorValue / 100 + "";
      }

      if (["+", "-", "/", "*"].includes(i)) {
        this.operator = i;
        this.previousCalculatorValue = this.calculatorValue;
        this.calculatorValue = "";
      }

      if (i === "=") {
        this.calculatorValue = eval(
          this.previousCalculatorValue + this.operator + this.calculatorValue
        );
        this.previousCalculatorValue = "";
        this.operator = null;
      }
    },
  },
};
</script>

<style>
body {
  background: #31475e !important;
}

.bg-vue-dark {
  background: #31475e;
}

.bg-vue-green {
  background: #3fb984;
}

.hover-class:hover {
  cursor: pointer;
  background: #3d5875;
}
</style>
