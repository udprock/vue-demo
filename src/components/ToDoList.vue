<template>
  <div class="ToDoList">
    <h1 v-text="title">My ToDoList</h1>
    <div>
      <input type="text" v-model="newItem">
      <button @click="addNewItem">添加</button>
    </div>
    <ul>
      <li v-for="item in items" :key="item.id">
        <span v-text="item.title"></span>
        <button v-on:click="toggleFinish(item)">完成</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'ToDoList',
  data () {
    return {
      title: 'ToDoList',
      items: [
        {
          id: 1,
          title: '吃'
        },
        {
          id: 2,
          title: 'drink'
        }
      ],
      id: 3,
      newItem: ''
    }
  },
  methods: {
    toggleFinish (recycleItem) {
      this.items.map((item, index) => {
        if (item.id === recycleItem.id) {
          this.items.splice(index, 1)
        }
      })
    },
    addNewItem () {
      this.items.push({
        id: this.id,
        title: this.newItem
      })
      this.id++
      this.newItem = ''
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: circle;
  padding: 0;
}
li {
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
