<script>
export default {
  data() {
    return {
      title: "ToDo List",
      tasks: [
        { name: "Выполнить лабораторную работу" },
        { name: "Помыть машину" },
        { name: "Погулять с собакой" },
      ],
    };
  }, 
  methods: {
    newItem: function () {
      if (!this.tasks.name) {
        return;
      }
      this.tasks.push({
        name: this.tasks.name,
        del: "",
      });
      this.tasks.name = "";
    },
    deleteItem: function (task) {
      this.tasks.splice(this.tasks.indexOf(task), 1);
    },
  },
}
</script>

<template>
<main class="container" id="tasklist">
    <h1 class="app-title">ToDo List</h1>
    <div class="add">
      <input type="text" autocomplete="off" placeholder="Добавить новую задачу..." class="task-input"
        v-model="tasks.name" @keyup.enter="newItem">
      <input type="submit" class="submit-task" @click="newItem" value="Добавить">
    </div>

    <ul class="task-list">
      <li class="task-list-item" v-for="task in tasks">
        <label class="task-list-item-label">
          <input type="checkbox">
          <span>{{task.name}}</span>
        </label>
        <button class="delete-btn" @click="deleteItem(task)">Удалить{{task.del}}</button>
      </li>
    </ul>

  </main>
</template>

<style>
  body {
  background-color: rgb(193, 158, 225);
  display:flex;
  justify-content: center;
  align-items: center;
  font-family: Tahoma, sans-serif;
}

input {
  outline: none;
}

ul {
  list-style: none;
  padding: 0;
}

.container {
  max-width: 500px;
  width: 100%;
  max-height: 100%;
  background-color: white;
  padding: 30px;
  margin-top: 80px;
  border-radius: 20px;
}

.add {
  height: 40px;
  font-size: 14px;
  display: flex;
}

.task-input {
  width: 100%;
  padding: 0 5px;
  outline: none;
  margin-right: 5px;
}

.task-list-item {
  display: flex;
  align-items: center;
  background-color: rgb(161, 96, 184);
  padding: 10px;
  margin-bottom: 5px;
  border-radius: 20px;
}

.delete-btn {
  margin-right: 5px;
  margin-left: auto;
  display: block;
  width: 60px;
  height: 20px;
  background-color: rgb(255, 255, 255);
  font-size: 10px;
  padding-right: 5px;
}
</style>