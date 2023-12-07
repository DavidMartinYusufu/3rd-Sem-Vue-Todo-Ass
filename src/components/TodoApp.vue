<template>
  <div class="body">
    <div class="container">
      <h2>Todo App</h2>

      <div class="">
        <div class="input-cnt">
          <input v-model="task" type="text" placeholder="Enter task" />
          <button class="add-btn" @click="submitTask">+</button>
        </div>

        <div class="item-container" v-for="(task, index) in tasks" :key="index">
          <div>{{ task.list }}</div>
          <div class="btn-container">
            <button class="btn-1" @click="editTask(index)">Edit</button>
            <button class="btn-1" @click="deleteTask(index)">x</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      task: "",
      editedTask: null,
      tasks: [
        {
          list: "Buy a book",
        },
      ],
    };
  },

  methods: {
    submitTask() {
      if (this.task.length === 0) return;

      if (this.editedTask === null) {
        this.tasks.push({
          list: this.task,
        });
      } else {
        this.tasks[this.editedTask].list = this.task;
        this.editedTask = null;
      }

      this.task = "";
    },

    deleteTask(index) {
      this.tasks.splice(index, 1);
    },

    editTask(index) {
      this.task = this.tasks[index].list;
      this.editedTask = index;
    },
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600&display=swap");

body {
  margin: 0%;
  background-color: #3f72af;
  padding: 0%;
  font-family: "Inter", sans-serif;
}

h2 {
  margin: 0%;
  padding-bottom: 15px;
}

input {
  border: none;
  padding: 6px;
  font-size: 16px;
  border-radius: 6px 0px 0px 6px;
  border: 1px solid rgb(219, 217, 217);
}

.add-btn {
  font-size: 20px;
  text-align: center;
  padding: 0px 10px 0px 10px;
  border-radius: 0px 6px 6px 0px;
  border: 1px solid rgb(219, 217, 217);
}

.input-cnt {
  display: flex;
  justify-content: center;
  margin-bottom: 30px;
}

button:focus {
  border: 1px solid rgb(161, 159, 159);
  background: rgb(224, 224, 224);
}

.container {
  margin: 0%;
  padding: 0%;
  text-align: center;
  background-color: #fff;
  padding: 20px;
  border-radius: 6px;
}

.body {
  display: flex;
  justify-content: center;
  max-width: 50%;
  margin: auto;
  margin-top: 30px;
}

.item-container {
  background-color: #dbe2ef;
  padding: 10px;
  border-radius: 6px;
  margin-top: 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  box-shadow: rgba(99, 99, 99, 0.2) 0px 2px 8px 0px;
}

.btn-container {
  display: flex;
  gap: 10px;
}

.btn-1 {
  border: 1px solid rgb(219, 217, 217);
  padding: 5px 10px 5px 10px;
  border-radius: 6px;
}
</style>
