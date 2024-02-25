<script>
// Create initial Input
const initialInput = {
  title: '',
  priority: false
}
export default {
  name: 'ListView',
  data: () => ({
    input: { ...initialInput },
    list: []
  }),
  methods: {
    // Reset Input when Task is Submitted
    resetInput() {
      Object.assign(this.input, initialInput)
    },
    //Submit Task
    onSubmit() {
      const data = {
        ...this.input,
        done: false
      }

      this.list.push(data)

      this.resetInput()
    },
    // Deleting Task
    onDelete(index) {
      if (index > -1) {
        this.list.splice(index, 1)
      }
    },
    // Mark as Done
    onSetDone(index) {
      this.list[index].done = !this.list[index].done
    },
    // Edit Task
    onEdit(index) {
      this.input = { ...this.list[index] }
      this.onDelete(index)
    },
    // Update Task
    onUpdate() {
      const data = {
        ...this.input,
        done: false
      }

      this.list.push(data)
      this.resetInput()
    }
  }
}
</script>

<template>
  <div>
    <form v-if="!editing" @submit.prevent="onSubmit">
      <input type="text" v-model="input.title" placeholder="Todo Title" />

      <div class="inline">
        <input
          type="checkbox"
          class="checkbox"
          id="priority"
          v-model="input.priority"
          placeholder="Todo"
        />
        <label for="priority"> High Priority</label>
      </div>

      <button type="submit">Submit</button>
    </form>

    <!-- Show the Item Task -->
    <div class="todo-list">
      <h2>ToDo List</h2>
      <ol>
        <div class="task-list">
          <li
            v-for="(item, index) in list"
            :key="index"
            @dblclick="onEdit(index)"
            @click="onSetDone(index)"
            class="task-item"
          >
            <div class="name-item">
              <input type="checkbox" v-model="item.done" class="checkbox" />
              <span :class="{ done: item.done, priority: item.priority }"
                >{{ item.title }}{{ item.priority ? ' - High' : '' }}</span
              >
            </div>
            <div class="button-item">
              <button @click="onEdit(index)" class="edit-button">Edit</button>
              <button @click="onDelete(index)" class="delete-button">Delete</button>
            </div>
          </li>
        </div>
      </ol>
    </div>
  </div>
</template>

<style lang="scss" scoped>
$primary-color: #24408e;
input:not([type='checkbox']) {
  width: 100%;
  padding: 10px;
  border: 1px solid $primary-color;
  border-radius: 5px;
  margin-bottom: 5px;
}
button {
  padding: 10px 20px;
  background-color: $primary-color;
  color: #fff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
.checkbox {
  margin-right: 10px;
}
.inline {
  display: flex;
  align-items: center;
  margin-bottom: 13px;
}
.todo-list {
  max-width: 100%;
  margin: 0 auto;
}
.task-list {
  list-style: none;
  padding: 0;
}
.task-item {
  display: flex;
  align-items: center;
  justify-content: space-between; /* Align items horizontally */
  padding: 10px;
  border-bottom: 1px solid $primary-color;
}
.priority {
  font-weight: bold;
  color: red; /* Change the color for high priority tasks */
}
.done {
  text-decoration: line-through;
  color: green;
}
.name-item {
  display: flex;
  align-items: center;
}
.button-item {
  display: flex;
  align-items: center;
}
.edit-button,
.delete-button {
  padding: 5px 10px;
  margin-left: 5px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s;
}
.edit-button:hover {
  background-color: gray;
}
.delete-button:hover {
  background-color: red;
}
</style>
