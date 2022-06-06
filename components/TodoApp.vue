<template>
  <div class="wrap">
    <h1 style="padding-top: 20px; color: white">Tasks For A Week</h1>
    <div class="main">
      <br />
      <input
        type="text"
        v-model.trim="text"
        @keyup.enter="add_task"
      /><br /><br />
      <div class="content" @scroll="scrollevent">
        <ul style="list-style: none">
          <li
            v-for="task in tasks"
            :key="task"
            v-bind:class="{ finished_item: task.done === true }"
          >
            <div class="content_text">
              <span style="user-select: none" @click="finish_task(task.id)">{{
                task.name
              }}</span>
            </div>
            <div class="content_btn">
              <button class="item_button" @click="delete_task(task.id)">
                Remove
              </button>
            </div>
          </li>
        </ul>
      </div>
      <button class="add_button" style="" @click="add_task">Add</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoApp",
  data() {
    return {
      text: "",
      tasks: [
        { id: 1, name: "Cake", done: false },
        { id: 2, name: "Cookies", done: false },
        { id: 3, name: "Pudding", done: false },
        { id: 4, name: "Chocolate", done: false },
        { id: 5, name: "Cheese", done: false },
        { id: 6, name: "Drinks", done: false },
        { id: 7, name: "Tea", done: false },
        { id: 8, name: "Coffee", done: false },
        { id: 9, name: "Cupcake", done: false },
      ],
    };
  },
  methods: {
    finish_task(taskId) {
      let task = this.tasks.find((item) => {
        return item.id === taskId;
      });
      task.done = !task.done;
      this.save_task();
    },

    delete_task(id) {
      const index = this.tasks.findIndex((tasks) => tasks.id === id);
      this.tasks.splice(index, 1);
      this.save_task();
    },

    add_task() {
      if (
        this.text.length === 0 ||
        this.text.replace(/(^s*)|(s*$)/g, "") == 0
      )
        return;

      this.tasks.push({
        id: this.tasks.length + 1,
        name: this.text,
        done: false,
      });
      this.text = "";
      this.save_task();
    },

    save_task() {
      let save_item = JSON.stringify(this.tasks);
      localStorage.setItem("tasks", save_item);
    },
  },
  mounted() {
    if (localStorage.getItem("tasks")) {
      try {
        this.tasks = JSON.parse(localStorage.getItem("tasks"));
      } catch (e) {
        localStorage.removeItem("tasks");
      }
    }
  },
};
</script>

<style scoped>
.item_button {
  position: relative;
  left: 60px;
  top: -20px;
  color: white;
  background-image: linear-gradient(rgb(35, 36, 85), rgb(145, 103, 155));
  border-radius: 7px;
}

.add_button {
  width: 200px;
  height: 8%;
  color: white;
  background-image: linear-gradient(rgb(35, 36, 85), rgb(145, 103, 155));
  border-radius: 7px;
}
</style>
