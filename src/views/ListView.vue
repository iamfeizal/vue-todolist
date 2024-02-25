<script>
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
  watch: {
    'input.question'(val) {
      if (val.includes('?')) {
        this.handleQuestion()
      }
    }
  },
  methods: {
    // log() {
    //     console.log(this.input)
    // },
    // handleQuestion(){
    //     console.log('Question:', this.input.question);
    // },
    resetInput() {
      Object.assign(this.input, initialInput)
    },
    onSubmit() {
      const data = {
        ...this.input,
        done: false,
      }

      this.list.push(data)

      this.resetInput()
    },
    onDelete(index){
        if (index > -1) {
            this.list.splice(index, 1)
        }
    },
    onSetDone(index){
        this.list[index].done = !this.list[index].done
    }
  }
}
</script>

<template>
  <div>
    <form @submit.prevent="onSubmit">
      <input type="text" v-model="input.title" placeholder="Todo Title" />

      <div class="inline">
        <input type="checkbox" id="priority" v-model="input.priority" placeholder="Todo" />
        <label for="priority">High Priority</label>
      </div>

      <button type="submit">Submit</button>
    </form>
    <!-- <input type="text" v-model="input.title" />
    
        <button>Log to console</button> -->
    <ol>
      <li v-for="(item, index) in list"
      :key="index"
      @dblclick="onDelete(index)"
      @click="onSetDone(index)"
      :class="{ done: item.done, priority: item.priority }"
      >{{ item.title }}{{ item.priority ? ' - High' : ''}}</li>
    </ol>
  </div>
</template>

<style lang="scss" scoped>
input:not([type='checkbox']) {
  height: 2rem;
  width: 100%;
}
button {
  height: 2rem;
}
.inline {
  display: flex;
  align-items: center;
}
div {
  display: grid;
}
.priority{
    font-weight: bold;
}
.done{
    text-decoration-line: line-through;
    color: hsla(160, 100%, 37%, 1);
}
</style>
