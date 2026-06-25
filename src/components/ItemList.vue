<!-- src/components/ItemList.vue -->
<script setup lang="ts">
import { ref } from 'vue'

interface Item {
  name: string
  price: number
}

const items = ref<Item[]>([
  { name: 'たまご', price: 100 },
  { name: 'りんご', price: 160 }
])
const newItemName = ref('') 
const newItemPrice = ref(0) 

const addItem = () => { 
    //入力欄が空なら追加されない(無料の商品なんてないよ)
    if(newItemName.value && newItemPrice.value){
        //追加しようとしている商品と同じ名前の商品がすでに存在すれば、追加しない。
        if(items.value.some((item) => item.name === newItemName.value)){

          return
        }
        items.value.push({ name: newItemName.value, price: newItemPrice.value }) 
        //商品を追加した後入力欄を空にする。
        newItemName.value = ''
        newItemPrice.value = 0
    }

}

const deleteItem = (name: string) => {
  items.value = items.value.filter((item) => item.name !== name)
    
}
</script>

<template>
  <div>
    <div>ItemList</div>
    <ul>
      <li v-for="item in items" :key="item.name" :class="{over500: item.price >= 500}">
        <div>名前: {{ item.name }}</div>
        <div>{{ item.price }} 円</div>
        <button @click="deleteItem(item.name)">削除</button>
      </li>
    </ul>
    <div>
      <label>
        名前
        <input v-model="newItemName" type="text" />
      </label>
      <label>
        価格
        <input v-model="newItemPrice" type="number" />
      </label>
      <button @click="addItem">追加</button>
    </div>
  </div>
</template>

<style>
  .over500{
    color :red;
  }
  </style>