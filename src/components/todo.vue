<template>
    <div id="app">
      
        
    <div class="main">
         <div>
            <button @click="clear" value="clear list" class="clear-value">clear list</button>
        </div>
    <div class="input-icons">
        <i class="fa fa-plus" />
        <input
          v-model="newText"
          class="input-field"
          type="text"
          placeholder="Enter Your Items"
          @keyup.enter="addTask"
        >
      </div>
    <div class="content"
        v-for="(task,index) in tasks"
        :key="index"
        >
        <label class="container">
        <input type="checkbox" v-model="task.done">
        <span class="checkmark"></span>
        <span :class="{'task-done': task.done }">
            {{ task.name }}
        </span>
        </label>
        </div>
    </div>
    </div>
</template>

<script>
export default {
    data (){
        return {
            newText: '',
            tasks:[
                { name:'this is first item', done: false},
                { name:'this is first second', done: false},
                { name:'this is first third', done: false}
            ],
        }
      
    },
     computed: {
    incomplete() {
      return this.tasks.filter(this.inProgress).length;
    }
  },
    methods: {
    addTask () {
      if (this.newText) {
        this.tasks.push({
          name: this.newText
        });
        this.newText = '';
      }
    },
    clear(){
        this.tasks = [ 


        ];
    }
  
    }
}
</script>

<style>
.main {
    border: 1px solid black;
    height: auto;
    width: 400px;
    padding: 10px;
    margin: 300px 300px 500px 800px;
}
.form-control{
    height: 30px;
    width: 300px;
}
.clear-value{
    color:aliceblue;
    background: #fb6f70;
    width: 100px;
    height: 30px;
    text-align: center;
    margin-left: 200px;
    font-weight: bold
}
.content{
    height: 20px;
    width: 290px;
    border: 1px solid black;
    margin: 20px 50px 20px 42px;
    padding: 10px;
    text-align: left;
    display: flex;
    justify-content: flex-start;
}
.fa{
    font-size: 25px;
    margin-left: 35px;
    
}
.additems{
    display: flex;
}

.input-field{
   width: 91%;
  padding-left: 30px;
  outline: none;
  border: 0px;
  font-size: 15px;
  font-weight: bold;
}
.input-icons {
  display: flex;
  width: 300px;
  padding: 15px;
  height:40px;
  align-items: center;
}
.task-done {
      text-decoration: line-through;
}
.backcolor {
    background: #fb6f70;
}


.container {
  display: block;
  position: relative;
  padding-left: 35px;
  margin-bottom: 12px;
  cursor: pointer;
  font-size: 22px;
  -webkit-user-select: none;
  -moz-user-select: none;
  -ms-user-select: none;
  user-select: none;
}

/* Hide the browser's default checkbox */
.container input {
  position: absolute;
  opacity: 0;
  cursor: pointer;
  height: 0;
  width: 0;
}

/* Create a custom checkbox */
.checkmark {
  position: absolute;
  top: 0;
  left: 0;
  height: 25px;
  width: 25px;
  background-color: #eee;
}

/* On mouse-over, add a grey background color */
.container:hover input ~ .checkmark {
  background-color: #ccc;
}

/* When the checkbox is checked, add a blue background */
.container input:checked ~ .checkmark {
   background: #fb6f70;
}

/* Create the checkmark/indicator (hidden when not checked) */
.checkmark:after {
  content: "";
  position: absolute;
  display: none;
}

/* Show the checkmark when checked */
.container input:checked ~ .checkmark:after {
  display: block;
}

/* Style the checkmark/indicator */
.container .checkmark:after {
  left: 9px;
  top: 5px;
  width: 5px;
  height: 10px;
  border: solid white;
  border-width: 0 3px 3px 0;
  -webkit-transform: rotate(45deg);
  -ms-transform: rotate(45deg);
  transform: rotate(45deg);
}
</style>
