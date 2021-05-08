<template>
  <q-page padding>
    <div class="row" q-mb-lg style="max-width: 450px">
        <q-input outlined v-model="newTask" placeholder="Add new task" class="col" @keyup.enter="addTask"/>
      <q-btn push color="primary" text-color="white" label="Add" @click.native="addTask" />
    </div>


     <div class="q-pa-lg" q-mb-lg style="max-width: 450px">
       <q-list-header> Tasks </q-list-header>
            <q-list bordered v-for="(task, index) in tasks" :key="index">
              <q-item >
                <q-item-section>{{task}}</q-item-section>
                <q-item-section avatar>
                  <q-icon color="primary" name="eva-checkmark-outline" @click.native="moveToDone(index)"/>
                </q-item-section>
              </q-item>
            </q-list>
     </div>

      <div class="q-pa-lg" style="max-width: 450px">
       <q-list-header> Done </q-list-header>
            <q-list bordered v-for="(task, index) in done" :key="index">
              <q-item >
                <q-item-section>{{task}}</q-item-section>
                <q-item-section avatar>
                  <q-icon color="red" name="eva-close-outline" @click.native="deleteTask(index)" />
                </q-item-section>
              </q-item>
            </q-list>
     </div>

  </q-page> 
</template>

<script>
          export default {
            name: 'PageIndex',
            data () {
              return{
                tasks:[],
                done:[],
                newTask:''
              }
            },
            methods:{
              addTask(){
                this.tasks.push(this.newTask)
                this.newTask=''
              },
              moveToDone(index){
                this.done.push(this.tasks[index]),
                this.tasks.splice(index, 1)
              },
              deleteTask(index){
              this.done.splice(index, 1)
            },
            }  
          }   
</script>