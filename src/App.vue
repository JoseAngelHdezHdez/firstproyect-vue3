<script setup>
import { ref, computed } from 'vue';

const name = "Vue dinamico";

const cont = ref(0);
const arrayNumbers = ref([]);

const increment = () => cont.value++;

const rest = () => cont.value--;

const del = () => (cont.value = 0);

const add = () => arrayNumbers.value.push(cont.value);

const valid = computed(() => {
  const numExist = arrayNumbers.value.find((num) => num === cont.value)
  console.log(numExist);
/*   if (numExist === 0) return true
  return numExist ? true : false; */
  return numExist || numExist === 0;
});

const classCounter = computed(() => {
  if (cont.value === 0) {
    return 'zero';
  }
  if (cont.value > 0) {
    return 'positive'
  }
  if (cont.value < 0) {
    return 'negative';
  }
});
</script>

<template>
  <div class="container text-center mt-3">
    <h1>Hola {{ name.toUpperCase() }}</h1>
    <div class="btn-group">
      <button @click="increment" class="btn btn-success"> Aumentar </button>
      <button @click="rest" class="btn btn-danger"> Disminuir </button>
      <button @click="del" class="btn btn-secondary"> Cero </button>
      <button @click="add" :disabled="valid" class="btn btn-primary"> Add </button>
    </div>
    <p :class="classCounter">{{ cont }}</p>
    <ul class="list-group mt-4">
      <li class="list-group-item" v-for="(num, index) in arrayNumbers" :key="index"> {{ num }} </li>
    </ul>
  </div>

</template>

<style>
h1 {
  color: red;
}

.positive {
  color: green;
}

.negative {
  color: red;
}

.zero {
  color: azure;
}
</style>