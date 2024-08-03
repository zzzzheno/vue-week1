<template>
  <table style="width: 100%">
    <thead>
      <tr>
        <th scope="col" :class="$style.thTitle" style="width: 60%">品項</th>
        <th scope="col" :class="$style.thTitle" style="width: 20%">價格</th>
        <th scope="col" :class="$style.thTitle" style="width: 20%">庫存</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="product in product">
        <td :class="$style.productName">
          {{ product.name }}
          <br />
          <small style="font-size: 0.875rem">{{ product.description }}</small>
        </td>
        <td :class="$style.productName">${{ product.price }}</td>
        <td>
          <button :class="$style.button" @click="product.amount--">-</button>
          <input type="text" :class="$style.productAmount" v-model="product.amount" />
          <button :class="$style.button" @click="product.amount++">+</button>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script setup>
import { ref } from 'vue'

const product = ref([
  {
    name: '珍珠奶茶',
    description: '香濃奶茶搭配QQ珍珠',
    price: 50,
    amount: 20
  },
  {
    name: '冬瓜檸檬',
    description: '清新冬瓜配上新鮮檸檬',
    price: 45,
    amount: 18
  },
  {
    name: '翡翠檸檬',
    description: '綠茶與檸檬的完美結合',
    price: 55,
    amount: 34
  },
  {
    name: '四季春茶',
    description: '香醇四季春茶，回甘無比',
    price: 45,
    amount: 10
  },
  {
    name: '阿薩姆奶茶',
    description: '阿薩姆紅茶搭配香醇鮮奶',
    price: 50,
    amount: 25
  },
  {
    name: '檸檬冰茶',
    description: '檸檬與冰茶的清新組合',
    price: 45,
    amount: 20
  },
  {
    name: '芒果綠茶',
    description: '芒果與綠茶的獨特風味',
    price: 55,
    amount: 18
  },
  {
    name: '抹茶拿鐵',
    description: '抹茶與鮮奶的絕配',
    price: 60,
    amount: 20
  }
])
</script>

<style module>
.thTitle {
  padding: 0.5rem 1rem;
  font-weight: 700;
  text-align: left;
  background-color: #cccccc;
}

.productName {
  font-size: 1.25rem;
  font-weight: 700;
  padding: 0.5rem 1rem;
}

.productAmount {
  width: 2.5rem;
  height: 1.5rem;
  margin: 0 0.25rem;
  font-size: 1rem;
  border: solid 1px #000000;
}

.button {
  height: 1.5rem;
  font-size: 1rem;
  text-align: center;
  background-color: #fff;
  border: solid 1px #000000;
  cursor: pointer;
}

.button:hover {
  background-color: #bababa;
  cursor: pointer;
}
</style>
