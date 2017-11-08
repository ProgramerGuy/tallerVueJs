<template>
  <div id="app">

<!-- Encabezado -->
    <div class="hero">
      <div class="hero-head">
        <nav class="navbar">
          <div class="container">
            <div class="navbar-brand">
              <div class="navbar-item">
                <img src="./assets/logo.png">
              </div>
            </div>
          </div>
        </nav>  
      </div>
    </div>

<!-- Formulario Crear Tareas -->

    <section class="container" v-show="!isEdit">
      <div class="panel create-panel">
        <div class="panel-heading">
          Crear tarea
        </div>
        <form @submit.prevent="addTask" >
          <div class="panel-block">
            <div class="control">
              <b-field label="Nombre">
                <b-input v-model:value="task.name"></b-input>
              </b-field>
            </div>
          </div>
          <div class="panel-block">
            <div class="control">
              <b-field label="Descripcion">
                <b-input v-model:value="task.description"></b-input>
              </b-field>
            </div>
          </div>
          <div class="panel-block">
            <div class="control">
              <b-field label="Detalle">
                <b-input v-model:value="task.detail" type="textarea"></b-input>
              </b-field>
            </div>
          </div>
          <div class="panel-block">
            <div class="control">
              <b-field label="Tiempo">
                <b-input v-model:value="task.time" type="number"></b-input>
              </b-field>
            </div>
          </div>
          <div class="panel-block panel-border">
            <div class="control">
              <input type="submit" value="Guardar" class="button is-primary is-fullwidth is-large">
            </div>
          </div>
        </form>
      </div>
    </section>

    <section class="container" v-show="isEdit">
      <div class="panel create-panel">
        <div class="panel-heading">
          Editar tarea
        </div>
        <form @submit.prevent="editTask" >
          <div class="panel-block">
            <div class="control">
              <b-field label="Nombre">
                <b-input v-model:value="task.name"></b-input>
              </b-field>
            </div>
          </div>
          <div class="panel-block">
            <div class="control">
              <b-field label="Descripcion">
                <b-input v-model:value="task.description"></b-input>
              </b-field>
            </div>
          </div>
          <div class="panel-block">
            <div class="control">
              <b-field label="Detalle">
                <b-input v-model:value="task.detail" type="textarea"></b-input>
              </b-field>
            </div>
          </div>
          <div class="panel-block">
            <div class="control">
              <b-field label="Tiempo">
                <b-input v-model:value="task.time" type="number"></b-input>
              </b-field>
            </div>
          </div>
          <div class="panel-block panel-border">
            <div class="control">
              <input type="submit" value="Editar" class="button is-primary is-fullwidth is-large">
            </div>
          </div>
        </form>
      </div>
    </section>
    
  <div class="container is-fullwidth ">
      <div class="columns is-multiline">
        <task class="column is-two-fifths" v-for="item in taskList" :task="item"> 
        </task>
      </div>
  </div>

  </div>

</template>

<script>
import Task from './components/Task'

export default {
  name: 'app',
  components: {
    Task,
  },
  data(){
    return{
      task: {
        name: "",
        description: "",
        detail: "",
        time: 0,
      },
      taskList: [],
      isEdit: true,
    }
  },
  methods: {
    addTask: function(){
      this.taskList.push(this.task)
      this.task = {}
    },
    editTask: function(){
      this.isEdit = false
    },
    selectedItem: function(item){
      this.task = item
    }
  },
  created() {
    window.bus.$on('selectedItem', this.selectedItem)
  },
}
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
  }

  .create-panel{
    width: 50%;
    margin-left: auto;
    margin-right: auto;
  }

  .panel-block{
    border-bottom: none;
  }

  .panel-border{
    border-bottom: 1px solid #dbdbdb;
  }
</style>
