<script>
const initialInput = {
    title: '',
    priority: false
}
export default {
    name: 'ListView',
    data: () => ({
        input: { ...initialInput},
        list: []
    }),
    watch: {
        'input.question'(val) {
            if (val.includes('?')){
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
        resetInput(){
            Object.assign(this.input, initialInput)
        },
        onSubmit(){
            const data = { ...this.input}

            this.list.push(data)

            this.resetInput()
        }
    }
}
</script>

<template>
    <div>
        <form @submit.prevent="onSubmit">
            <input type="text" v-model="input.title" placeholder="Todo Title">
    
            <div class="inline">
                <input type="checkbox" id="priority" v-model="input.priority" placeholder="Todo">
                <label for="priority">High Priority</label>
            </div>
    
            <button type="submit">Submit</button>
        </form>
        <!-- <input type="text" v-model="input.title" />
    
        <button>Log to console</button> -->
        <ol>
            <li v-for="(item, index) in list" :key="index">{{ item }}</li>
        </ol>
    </div>
</template>

<style lang="scss" scoped>
    input:not([type=checkbox]) {
        height: 2rem;
        width: 100%;
    }
    button{
        height: 2rem;
    }
    .inline{
        display: flex;
        align-items: center;
    }
    div{
        display: grid;
    }
</style>