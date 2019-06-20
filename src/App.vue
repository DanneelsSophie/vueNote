<template>
  <div id="app">
    <ol>
      <li v-for="todo in todos" v-bind:key="todo.id"  >
        {{ todo.text }}
        <button v-on:click="del(todo.id) ">delete a note</button>

      </li>
    </ol>
    <input v-model="message" placeholder="modifiez-moi">
    <p>Your futur todo is : {{ message }}</p>
    <button v-on:click="add ">Add a note</button>

  </div>
</template>

<script>
    export default {
        name: 'app',
        data () {
            return {
                message:'',
                todos: [
                    { text: 'Apprendre JavaScript', id:0 },
                    { text: 'Apprendre Vue', id:1 },
                    { text: 'Créer quelque chose de génial', id:2 }
                ],
                counter: 3
            }
        },
        methods: {
            add() {
                this.counter++;
                this.todos.push({text: this.message,id:this.counter})
            },
            del(id) {
                this.todos = this.todos.filter(todo => todo.id != id);
            }
        }
    }
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>