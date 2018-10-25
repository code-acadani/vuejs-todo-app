<template>
  <div class="home">

		<h1>Todo List: </h1>

		<div>
	    <button v-on:click="removeCompletedTasks()">Clear Completed Tasks</button>
	  </div>

	  <button v-on:click="toggleTaskFilter(false)">View Incomplete</button>
	  <button v-on:click="toggleTaskFilter(true)">View Complete</button>
	  <button v-on:click="toggleTaskFilter('all')">View All</button>

	  <div>
	  	Search Tasks: <input v-model="taskFilter" list="taskText">
	  </div>

	  <datalist id="taskText">
	  	<option v-for="task in tasks">{{ task.text }}</option>
	  </datalist>

    <div v-for="task in filterBy(tasks, taskFilter)" v-on:click="toggleCompleted(task)">
      <h4 :class="{strike: task.completed}"> {{ task.text }} </h4>
    </div>

  </div>
</template>

<style>
	.strike {
		text-decoration: line-through;
	}
</style>

<script>
export default {
  data: function() {
    return {
      tasks: [
      	{
      		id: 1,
      		text: "Mow the lawn",
      		completed: false
      	},
      	{
      		id: 2,
      		text: "Brush the cat",
      		completed: true
      	},
      	{
      		id: 3,
      		text: "Eat your veggies",
      		completed: false
      	},
      	{
      		id: 4,
      		text: "Do the dishes",
      		completed: false
      	},
      	{
      		id: 5,
      		text: "Learn to code",
      		completed: false
      	}
      ],
      taskFilter: ''
    };
  },
  methods: {
    toggleCompleted: function(task) {
      task.completed = !task.completed;
    },
    removeCompletedTasks: function() {
	    var incompleteTasks = [];
	    this.tasks.forEach(function(task){
	    	if (!task.completed) {
	        incompleteTasks.push(task);
	      }
	    });
	    this.tasks = incompleteTasks;
    },
    toggleTaskFilter: function(filter) {
    	if(filter === true) {
    		this.taskFilter = true;
    	} else if(filter === 'all'){
    		this.taskFilter = '';
    	} else {
    		this.taskFilter = false;
    	}
    }
  },
  computed: {}
};
</script>
















