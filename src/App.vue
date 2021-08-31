<template>
<div>
  <h1 class="title">{{ title }}</h1>
  <div class="todo">
    <p>{{ todo }}</p>
    <input v-model="todo" type="text" placeholder="Введите значение..."/>
    <button type="button" @click="addTodo(id++)" class="btn btn-info">Добавить</button>
    <div v-for="todo in todos" :key="todo.id">
      <p>
        <span class="todo__id"> {{ todo.id }} </span>
        <span class="todo__text" :class = "{todo__text_isShow: todoisDone} "> {{ todo.text }} </span>
        <input v-model="todo.isComplete" class="todo__check" type="checkbox" />
      </p>
    </div>
  </div>
</div>
</template>

<script>


export default {
  data: function () {
    return {
      title: "ToDo App",
      todo: "",
      todos: [],
      isDone: false,
      id: 0
    }
  },
  methods: {
    addTodo () {
      this.todos.push({
        id: this.id,
        text: this.todo,
        isComplete: this.isDone
      });
      this.todo = "";
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.btn-info {
  margin-left: 5px;
}
.todo__id{
  margin-right: 5px;
  font-weight: bold;
}
.todo__text{
  font-size: 15px;
  color: darkslateblue;
  text-transform: capitalize;
}
.todo__text_isShow {
  color: #ccc;
  text-decoration: line-through;
}

.todo__check {
  display:inline-block;
  margin-left: 10px;
}

</style>
