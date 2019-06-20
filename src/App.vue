<template>
  <v-app>
  <div id="app">
    <ol>
      <li v-for="todo in todos" v-bind:key="todo.id"  >
        {{ todo.text }}
        <v-btn  fab dark small v-on:click="del(todo.id)" color="error">
          <v-icon dark>remove</v-icon>
        </v-btn>

      </li>
    </ol>
    <v-flex xs10 offset-xs1>
      <v-text-field
              v-model="message" placeholder="modifiez-moi"
              label="Solo"
              solo
      ></v-text-field>
    </v-flex >
    <div  class="text-xs-center">
      <p>Your futur todo is : {{ message }}</p>
      <v-btn  v-on:click="add " fab dark small color="success">
        <v-icon dark>add</v-icon>
      </v-btn>
    </div>

  </div>
    </v-app>
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