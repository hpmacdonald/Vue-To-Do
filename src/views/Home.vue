<template>
  <div class="home pa-6">
    <h1>Home Page</h1>
          <v-subheader>Create your to-do list below</v-subheader>
      <v-text-field
        v-model="newTaskTitle"
        @click:append="addTask"
        @keyup.enter="addTask"
        class="pa-2 bv"
        outlined
        label="Create New Task"
        append-icon="mdi-plus-circle"
        hide-details
        clearable
      ></v-text-field>
    <v-list
      subheader
      two-line
      flat
    >


      <v-list-item-group
        v-model="settings"
        multiple
      >
      <div v-for="task in tasks"
        :key="task.id"

        >
        <v-list-item 
        @click="doneTask(task.id)"
        :class="{ 'purple' : task.done }"
        >
          <template v-slot:default >
            <v-list-item-action>
              <v-checkbox
                :input-value="task.done"
                color="primary"
              ></v-checkbox>
            </v-list-item-action>

            <v-list-item-content>
              <v-list-item-title
              :class="{ 'text-decoration-line-through' : task.done }"
              >{{task.title}}</v-list-item-title>
              <v-list-item-subtitle>Allow notifications</v-list-item-subtitle>
            </v-list-item-content>

            <v-list-item-action>
            <v-btn 
            @click.stop="deleteTask(task.id)"
            icon>
              <v-icon color="primary lighten-1"
              :loading="loading"
              > mdi-delete </v-icon>
            </v-btn>
          </v-list-item-action>
          </template>

          

        </v-list-item>
        <v-divider></v-divider>
      </div>
        
      </v-list-item-group>
    </v-list>
  </div>
</template>


<script>
export default {
  name: 'Home',
  data() {
    return {
      newTaskTitle: '',
      tasks: [
        {
          id: 1,
          title: 'Wake up',
          done: false
        },
        {
          id: 2,
          title: 'Eat Snacks',
          done: false
        },
     
      ]
    }
  },
  methods: {
    addTask() {
      let newTask = {
        id: Date.now(),
        title: this.newTaskTitle,
        done: false
      }
      this.tasks.push(newTask)
      this.newTaskTitle = ''
    },
    doneTask(id) {
      let task = this.tasks.filter(task => task.id === id)[0]
      task.done = !task.done
    },
    deleteTask(id) {
       this.tasks = this.tasks.filter(task => task.id !== id)
    }
  }
}
</script>