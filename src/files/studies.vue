<script setup>
const name = "Vue dinamico";
const styleColor = "color: blue";
const arrayColores = ["blue", "red", "peru"];
const activo = false;
const arrayFrutas = ["🍎", "🍌", "🍉", "🍓", "🍒"];
const Frutas = [
  {
    name: "Manzana",
    price: "$1.00",
    description: "Una manzana",
    stock: 0
  },
  {
    name: "Pera",
    price: "$2.00",
    description: "Una pera",
    stock:
      10
  },
  {
    name: "Naranja",
    price: "$3.00",
    description: "Una naranja",
    stock: 20
  },
];
const objFruta = {
  name: "Naranja",
  price: "$3.00",
  description: "Una naranja",
  stock: 20
}; 
</script>

<template>
  <h1>Hola {{ name.toUpperCase() }}</h1>
  <h2>{{ arrayColores }}</h2>
  <h2 :style="`color: ${arrayColores[0]}`">Soy azul</h2>
  <h3>
    {{ activo ? "Estoy activo" : "Estoy inactivo" }}
  </h3>
  <p v-if="activo">Estoy activo</p>
  <p v-if="!activo">Estoy inactivo</p>

  <h2 v-show="activo">Estoy activo v-show</h2>

  <ul>
    <li v-for="(fruta, index) in arrayFrutas" :key="index"> {{ index }} - {{ fruta }} </li>
  </ul>

  <ul>
    <li v-for="(fruta, index) in Frutas" :key="fruta.name"> {{ fruta.name }} - {{ fruta.price }} - {{ fruta.description
    }} </li>
  </ul>

  <ul>
    <li v-for="(value, propiedad, index) in objFruta" :key="value"> {{ index }} - {{ propiedad.toUpperCase() }}: {{ value
    }} </li>
  </ul>

  <ul>
    <template v-for="item in  Frutas" :key="item.name">      
      <li v-if="item.stock > 0"> 
        {{ item.name }}-> {{ item.price }}  
      </li>
    </template>
  </ul>
</template>

<style>
h1 {
  color: red;
}
</style>