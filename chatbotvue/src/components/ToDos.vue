<template>
    <div id="todosapp">
        <div class="block">
            <div class="todolist" v-for="todolist in todolists" :key="todolist.id" @click="openlist(todolist.id - 1)">
                {{todolist.title}}
            </div>
            <div class="addlist">
                <input type="text" placeholder="Dodaj Listę" v-model="newlist"/>
                <button @click="addlist">⁺</button>
            </div>
        </div>
        <div class="block">
            <ToDo :list="openedlist" @DoneClicked="done" @DelClicked="del" @AddClicked="add"/>
        </div>
    </div>
</template>

<script>
    import ToDo from "./ToDo.vue";

    let TodoLists = [
                        { 
                            title: "Przykładowa lista", 
                            done: false, 
                            content: 
                            [
                                {
                                    title: "Test",
                                    completed: false,
                                    id: 1
                                }
                            ],
                            id: 1
                        }
                    ]

    export default {
        components: {
            ToDo
        },
        data() {
            return {
                newlist: "",
                todolists: TodoLists
                ,
                openedlist: TodoLists[0]
            }
        },
        methods: {
            addlist(){
                TodoLists.push({ title: this.newlist, done:false, content: [], id: (this.todolists.length + 1)})
                this.newlist = ""
            },
            openlist(id) {
                this.openedlist = TodoLists[id]
            },
            done(id) {
                this.openedlist.content[id].completed = true
            },
            del(id) {
                this.openedlist.content.splice(id, 1)
            },
            add(title){
                this.openedlist.content.push({title: title, completed: false, id: (this.openedlist.content.length + 1)})
            }
        }
    }
</script>

<style>
    #todosapp{
        min-height: 700px;
    }
    .block{
        width: calc(70% - 1px);
        min-height: 700px;
        float: left;
    }
    .block:first-child{
        width: 30%;
        background-color: #ccc29b;
        border-right:1px solid #303030;
    }
    .todolist{
        width: calc(90% - 6px - 50px);
        height: calc(80px - 6px - 50px);
        border:3px dotted #b5ad7f;
        padding:25px;
        margin:10px 5%;
        border-radius:35px 0;
        font-size:24px;
        color: #605b3d;
        letter-spacing: 0.1em;
        font-weight: 600;
        font-style: normal;
        transition: all 0.5s linear 100ms;
    }
    .todolist:hover{
        background-color: #b5ad7f;
        border:solid;
        cursor: pointer;
    }
    .addlist{
        width: 90%;
        height: 70px;
        margin:10px 5%;
        border-radius:35px 0;
        opacity: 0.75;
    }
    .addlist input{
        width: calc(75% - 4px - 20px);
        height: calc(70px - 4px);
        font-size: 26px;
        padding: 0 20px;
        border-radius: 35px 0 0 0;
        float: left;
        border: 2px solid #303030;
    }
    .addlist input{
        width: calc(80% - 4px - 40px);
        height: calc(70px - 4px);
        font-size: 26px;
        padding: 0 20px;
        border-radius: 35px 0 0 0;
        float: left;
        border: 2px solid #303030;
    }
    .addlist input:focus{
        box-shadow: 0px 0px 3px 3px #ffffffb5;
        outline:none;
    }
    .addlist button{
        width:20%;
        height:70px;
        border-radius: 0 0 35px 0;
        border:none;
        padding: 0;
        color: white;
        font-size: 68px;
        background-color: #303030;
        transition: all 0.5s linear 100ms;
    }
    .addlist button:hover {
        background-color: black;
        cursor: pointer;
    }
</style>