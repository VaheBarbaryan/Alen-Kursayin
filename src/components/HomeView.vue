<script setup>
import { ref } from 'vue';

const matrixResult = ref('')
const n = ref(null)

function matrix(n) {
  let result = ''
  const results = [];
  for(let i = 0; i < n; i++){
  results.push([]);
  }
  let startRow = 0;
  let endRow = n - 1;
  let startCol = 0;
  let endCol = n - 1;
  let count = 1;
  while(startRow <= endRow && startCol <= endCol){
  //top row
    for(let i = startCol; i <= endCol; i++){
      results[startRow][i] = count;
      count++;
    }
    startRow++
    //right column
    for(let i = startRow; i <= endRow; i++) {
      results[i][endCol]= count;
      count++;
    }
    endCol--;
    //bottom row
    for(let i = endCol; i >= startCol; i--){
      results[endRow][i] = count;
      count++;
    }
    endRow--;
    //left column
    for(let i = endRow; i >= startRow; i--){
      results[i][startCol] = count;
      count++;
    }
    startCol++;
  }

  for(let i = 0; i < n; i++) {
    for(let j = 0; j < n; j++) {
      result += `${results[i][j]} `
    }
    result += '\n';
  }
  matrixResult.value = result
}
</script>

<template>
  <h1>Սպիրալաձև մատրից</h1>
  <form class="form">
    <div class="form__row">
      <label for="number" class="form__label"></label>
      <input v-model="n" type="text" id="number" class="form__input">
    </div>
    <button type="button" @click="matrix(n)">Հաստատել</button>
  </form>
  <pre>{{ matrixResult }}</pre>
</template>

<style scoped>
input {
  width: 100%;
  max-width: 300px;
        margin:15px 0;
        padding:15px 10px;
        width:100%;
        outline:none;
        border:1px solid #bbb;
        border-radius:20px;
        display:inline-block;
        -webkit-box-sizing:border-box;
        -moz-box-sizing:border-box;
        box-sizing:border-box;
        -webkit-transition:0.2s ease all;
        -moz-transition:0.2s ease all;
        -ms-transition:0.2s ease all;
        -o-transition:0.2s ease all;
        transition:0.2s ease all;
        &:focus {
            border-color:cornflowerblue;
        }
    }
</style>