<template>
    <div id="todoContainer">
        <h1>Welcome to your To-do list</h1>
        <form @submit.prevent="addTask">
            <input type="text" placeholder="Enter a new task todo..." v-model="task" required />
            <p class="description"> Press 'Enter' to add the task. </p>
        </form>

        <ul>
            <li v-for="(data, index) in tasks" :key="index" :class="{ done: data.done  }">
                <span>{{ data.task }}</span>
                <div class="options">
                    <a href="#" class="done" @click.prevent="taskDone(index)" v-if="!data.done"><svg xmlns="http://www.w3.org/2000/svg" fill="currentColor" class="bi bi-check-circle" viewBox="0 0 16 16"><path fill-rule="evenodd" d="M8 15A7 7 0 1 0 8 1a7 7 0 0 0 0 14zm0 1A8 8 0 1 0 8 0a8 8 0 0 0 0 16z"/><path fill-rule="evenodd" d="M10.97 4.97a.75.75 0 0 1 1.071 1.05l-3.992 4.99a.75.75 0 0 1-1.08.02L4.324 8.384a.75.75 0 1 1 1.06-1.06l2.094 2.093 3.473-4.425a.236.236 0 0 1 .02-.022z"/></svg></a>
                    <a href="#" class="cancel" v-else @click.prevent="taskUndone(index)"><svg xmlns="http://www.w3.org/2000/svg" fill="currentColor" class="bi bi-x-circle" viewBox="0 0 16 16"><path fill-rule="evenodd" d="M8 15A7 7 0 1 0 8 1a7 7 0 0 0 0 14zm0 1A8 8 0 1 0 8 0a8 8 0 0 0 0 16z"/><path fill-rule="evenodd" d="M4.646 4.646a.5.5 0 0 1 .708 0L8 7.293l2.646-2.647a.5.5 0 0 1 .708.708L8.707 8l2.647 2.646a.5.5 0 0 1-.708.708L8 8.707l-2.646 2.647a.5.5 0 0 1-.708-.708L7.293 8 4.646 5.354a.5.5 0 0 1 0-.708z"/></svg></a>
                    <a href="#" class="delete" @click.prevent="deleteTask(index)" ><svg xmlns="http://www.w3.org/2000/svg" fill="currentColor" class="bi bi-trash" viewBox="0 0 16 16"><path d="M5.5 5.5A.5.5 0 0 1 6 6v6a.5.5 0 0 1-1 0V6a.5.5 0 0 1 .5-.5zm2.5 0a.5.5 0 0 1 .5.5v6a.5.5 0 0 1-1 0V6a.5.5 0 0 1 .5-.5zm3 .5a.5.5 0 0 0-1 0v6a.5.5 0 0 0 1 0V6z"/><path fill-rule="evenodd" d="M14.5 3a1 1 0 0 1-1 1H13v9a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V4h-.5a1 1 0 0 1-1-1V2a1 1 0 0 1 1-1H6a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1h3.5a1 1 0 0 1 1 1v1zM4.118 4L4 4.059V13a1 1 0 0 0 1 1h6a1 1 0 0 0 1-1V4.059L11.882 4H4.118zM2.5 3V2h11v1h-11z"/></svg></a>
                </div>
            </li>
        </ul>
    </div>
</template>

<script>

export default {
    name: "Todo",
    props: {},
    data() {
        return {
            task: "",
            tasks: [
            { "task": "Clean house", "done": false },
            { "task": "Eat breakfast", "done": true },
            { "task": "Go to the gym", "done": false }
        ]
        }
    },
    methods: {
        addTask() {
            this.tasks.push({ task: this.task, done: false });
            this.task = '';
        },
        deleteTask(index){
            this.tasks.splice(index, 1);
        },
        taskDone(index) {
            this.tasks[index].done = true;
        },
        taskUndone(index) {
            this.tasks[index].done = false;
        }
    }
}
</script>

<style scoped>
    #todoContainer{
         width: 500px;
         min-height: 500px;
         display: block;
         background: #FFF;
         margin: 0 auto;
         border-radius: 10px;
         box-shadow: 10px 10px 30px 0 rgba(0,0,0,0.05);
    }

    #todoContainer h1 {
        text-align: left;
        padding: 20px;
        font-size: 25px;
        background: #35495e;
        color: #FFF;
        border-radius: 10px 10px 0 0;
    }

    #todoContainer input {
        display: block;
        line-height: 50px;
        width: 100%;
        padding: 0 10px;
        border: 0;
        background: #f9f9f9;
        border-bottom: 1px #f1f1f1 solid;
        outline: 0;
    }

    #todoContainer ul { margin: 0;padding:0;list-style: none;padding: 10px; }
    #todoContainer ul li {
        text-align:left;
        padding: 10px;
        border-bottom: 1px #f1f1f1 solid;
        display: flex;
    }

    #todoContainer ul li.done {
        text-decoration: line-through;
        color: #CCC;
    }

    #todoContainer ul li:last-child { border-bottom: 0; }

    #todoContainer ul li span { width: 100%; }
    #todoContainer ul li .options { flex-shrink: 0; }
    #todoContainer ul li .options a {
        display: inline-block;
        margin-left: 5px;
    }
    #todoContainer ul li .options a svg { vertical-align: middle;width: 20px;height: 20px; }

    #todoContainer ul li .options a.done { color: rgb(110, 187, 33); }
    #todoContainer ul li .options a.delete { color: rgb(221, 84, 21); }
    #todoContainer ul li .options a.cancel { color: #4690de; }

    form .description {
        display: block;
        text-align:center;
        padding: 10px;
        font-size: 13px;
        background: #ffff002e;
        border-bottom: 1px #f9f982 solid;
    }
</style>