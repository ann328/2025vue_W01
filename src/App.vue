<script setup>
import { ref } from 'vue';
const array = ref([
  {
    id: 1,
    name: "珍珠奶茶",
    description: "香濃奶茶搭配QQ珍珠",
    price: 50,
    stock: 20
  },
  {
    id: 2,
    name: "冬瓜檸檬",
    description: "清新冬瓜配上新鮮檸檬",
    price: 45,
    stock: 18
  },
  {
    id: 3,
    name: "翡翠檸檬",
    description: "綠茶與檸檬的完美結合",
    price: 55,
    stock: 34
  },
  {
    id: 4,
    name: "四季春茶",
    description: "香醇四季春茶，回甘無比",
    price: 45,
    stock: 10
  },
  {
    id: 5,
    name: "阿薩姆奶茶",
    description: "阿薩姆紅茶搭配香醇鮮奶",
    price: 50,
    stock: 25
  },
  {
    id: 6,
    name: "檸檬冰茶",
    description: "檸檬與冰茶的清新組合",
    price: 45,
    stock: 20
  },
  {
    id: 7,
    name: "芒果綠茶",
    description: "芒果與綠茶的獨特風味",
    price: 55,
    stock: 18
  },
  {
    id: 8,
    name: "抹茶拿鐵",
    description: "抹茶與鮮奶的絕配",
    price: 60,
    stock: 20
  }
]);
const clickChamgeStock = function (item, str) {
  if (str === 'add') {
    item.stock++;
  } else if (str === 'reduce') {
    item.stock--;
  }
};
const editId = ref(null);
const editName = ref("");
const edit = function (item) {
  editId.value = item.id;
  editName.value = item.name;
};
const saveEdit = function (item) {
  editId.value = null;
  item.name = editName.value;
};
const cancelEdit = function () {
  editId.value = null;
};


</script>

<template>
  <h2>六角學院 2024 Vue 前端新手營</h2>
  <h3>Week1 作業</h3>
  <hr>
  <table>
    <thead>
      <tr>
        <th scope="col">品項</th>
        <th scope="col">描述</th>
        <th scope="col">價格</th>
        <th scope="col">庫存</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(item, key) in array" :key="item.id">
        <td scope="col" @dblclick="edit(item)">
          <span v-if="editId === item.id">
            <input v-model="editName" autofocus />
            <button @click="saveEdit(item)">儲存
            </button>
            <button @click="cancelEdit">取消</button>
          </span>
          <span v-else>{{ item.name }}</span>
        </td>
        <td scope="col">{{ item.description }}</td>
        <td scope="col">{{ item.price }}</td>
        <td scope="col">
          <button type="button" @click="clickChamgeStock(item, 'add')">+</button>
          {{ item.stock }}
          <button type="button" @click="clickChamgeStock(item, 'reduce')">-</button>
        </td>
      </tr>
    </tbody>
  </table>
  <hr>
</template>

<style scoped>
td,
tr {
  padding: 12px 40px;
}

button {
  margin: 4px;
}
</style>