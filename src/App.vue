<template>
  <div>
    <h3 style="font-weight: 700">品項管理</h3>
    <form action="">
      <div>
        <label for="name">品項</label>
        <input
          type="text"
          name="name"
          placeholder="請輸入品項"
          :class="$style.addProductInput"
          v-model="tempEdit.name"
        />
      </div>
      <div>
        <label for="describe">描述</label>
        <input
          type="text"
          name="describe"
          placeholder="請輸入描述"
          :class="$style.addProductInput"
          v-model="tempEdit.description"
        />
      </div>
      <div>
        <label for="price">價格</label>
        <input
          type="number"
          name="price"
          placeholder="請輸入價格"
          :class="$style.addProductInput"
          v-model="tempEdit.price"
        />
      </div>
      <div>
        <label for="amount">庫存</label>
        <input
          type="number"
          name="amount"
          placeholder="請輸入庫存"
          :class="$style.addProductInput"
          v-model="tempEdit.amount"
        />
      </div>
      <button type="button" :class="$style.button">送出</button>
    </form>
  </div>
  <table style="width: 100%">
    <thead>
      <tr>
        <th scope="col" :class="$style.thTitle" style="width: 50%">品項</th>
        <th scope="col" :class="$style.thTitle" style="width: 10%">價格</th>
        <th scope="col" :class="$style.thTitle" style="width: 20%">庫存</th>
        <th scope="col" :class="$style.thTitle" style="width: 20%">操作</th>
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
        <td style="text-align: center">
          <button type="button" :class="$style.button" @click="prepareEdit(product)">編輯</button>
          <button type="button" :class="$style.button">刪除</button>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script setup>
import { ref } from 'vue'
// 品項
const product = ref([
  {
    id: 1,
    name: '珍珠奶茶',
    description: '香濃奶茶搭配QQ珍珠',
    price: 50,
    amount: 20
  },
  {
    id: 2,
    name: '冬瓜檸檬',
    description: '清新冬瓜配上新鮮檸檬',
    price: 45,
    amount: 18
  },
  {
    id: 3,
    name: '翡翠檸檬',
    description: '綠茶與檸檬的完美結合',
    price: 55,
    amount: 34
  },
  {
    id: 4,
    name: '四季春茶',
    description: '香醇四季春茶，回甘無比',
    price: 45,
    amount: 10
  },
  {
    id: 5,
    name: '阿薩姆奶茶',
    description: '阿薩姆紅茶搭配香醇鮮奶',
    price: 50,
    amount: 25
  },
  {
    id: 6,
    name: '檸檬冰茶',
    description: '檸檬與冰茶的清新組合',
    price: 45,
    amount: 20
  },
  {
    id: 7,
    name: '芒果綠茶',
    description: '芒果與綠茶的獨特風味',
    price: 55,
    amount: 18
  },
  {
    id: 8,
    name: '抹茶拿鐵',
    description: '抹茶與鮮奶的絕配',
    price: 60,
    amount: 20
  }
  // 品項
])

const tempEdit = ref({
  id: '',
  name: '',
  description: '',
  price: '',
  amount: ''
})

const prepareEdit = (product) => {
  tempEdit.value = { ...product } // 拷貝，避免連動
  console.log(tempEdit.value)
}
</script>

<style module>
.addProductInput {
  height: 1.5rem;
  margin: 0 0.25rem;
  font-size: 1rem;
  border: solid 1px #000000;
}

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
