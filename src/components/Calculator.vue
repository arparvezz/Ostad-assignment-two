<script setup>
import { ref } from 'vue';
let firstNumber = ref('')
let lastNumber = ref('')
let operation = ref('')

function calculation() {
  let n1 = Number(firstNumber.value)
  let n2 = Number(lastNumber.value)
  let sign = operation.value

  // show output on submit
  document.getElementById('output').innerText = eval(`${n1} ${sign} ${n2}`)
}
</script>

<template>
  <div class="container mx-auto">
    <div class="sm:w-full md:w-1/3 lg:w-1/3 mx-auto m-5 p-3 rounded border bg-slate-50">
      <h2 class="text-2xl"><code>{Calculator/} </code> Project</h2>
      <!-- output display -->
      <div class="p-4 bg-slate-200 rounded">
        <div id="output">{{ firstNumber }} {{ operation }} {{ lastNumber }}</div>
      </div>

      <div class="my-1 p-4 bg-slate-400 rounded">
        <div class="flex space-x-1">
          <!-- first input box -->
          <input class="w-1/2 p-2 bg-slate-300 rounded outline-none border-none" type="number" name="first_number"
            placeholder="Enter first number" v-model="firstNumber">

          <!-- Second input box -->
          <input class="w-1/2 p-2 bg-slate-300 rounded outline-none border-none" type="number" name="second_number"
            placeholder="Enter Second number" v-model="lastNumber"><br>
        </div>

        <div class="my-1 space-x-1">
          <!-- Operation sign goes here -->
          <label for="sign">Select Operation</label>
          <select class="p-1 outline-none border-none rounded" name="sign" v-model="operation">
            <option value="+">+</option>
            <option value="-">-</option>
            <option value="*">*</option>
            <option value="/">/</option>
          </select>

          <!-- return calculation result function -->
          <button @click="calculation()"
            class="px-2 py-1 rounded outline-none border-none bg-blue-200 hover:bg-blue-300 cursor-pointer">Submit</button>

        </div>
      </div>
    </div>
  </div>
</template>

