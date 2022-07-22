<template>
    <div id="todoapp">
        <div class="todoitems">
            <div class="todoitem" v-for="item in list.content" :key="item.id" :class="{completed: item.completed}">
                <h1 class="todoitem-title">
                    {{item.title}}
                </h1>
                <button class="done" @click="done(item.id)" v-if="!item.completed">Zrobione!</button>
                <button class="done" @click="del(item.id)" v-else>Usuń!</button>
            </div>
        </div>
        <div class="todoadditem">
            <input type="text" placeholder="Nazwa zadania" v-model="newitem"/>
            <button @click="add">Dodaj Zadanie!</button>
        </div>
    </div>
</template>

<script>
    export default {
        props: ['list'],
        data() {
            return {
                newitem: ""
            }
        },
        methods: {
            done(id) {
                this.$emit('DoneClicked', (id - 1))
            },
            del(id) {
                this.$emit('DelClicked', (id - 1))
            },
            add(){
                if(this.newitem === ""){
                    alert("Nie wpisano nazwy")
                }
                else{
                    this.$emit('AddClicked', this.newitem)
                    this.newitem = ""
                }
            }
        }
    }
</script>

<style>
    .todoitems {
        width: calc(75% - 80px);
        min-height: calc(700px - 80px);
        float: left;
        padding:40px;
    }
    .todoadditem {
        width: calc(25% - 40px - 1px);
        min-height: calc(700px - 40px);
        background-color: #6f6f6f;
        float: left;   
        padding:20px;
        border-left:1px solid #303030;
        text-align:center;
    }
    .todoitem{
        width: calc(100% - 20px);
        height: calc(120px - 20px);
        background-color: #303030;
        padding:10px;
        border-radius:35px 0;
        text-align: center;
        margin:20px 0;
    }
    .todoitem-title {
        color: #fff;
        line-height: 0.2;
        letter-spacing: 0.1em;
        font-size: 40px;
        font-weight: 500;
        font-style: normal;
        height:10px;
        margin:25px 0;
    }
    .done{
        width: 50%;
        height: 40px;
        background-color: #7dc300;
        border:1px solid #669f00;
        border-radius:25px 0;
        color: white;
        font-size: 22px;
        line-height: 1;
        letter-spacing: 0.1em;
        font-weight: 600;
        transition: all 0.5s linear 100ms;
    }
    .done:hover{
        background-color: #3b5b00;
        border-color: #142000;
        cursor: pointer;
    }
    .completed h1{
        text-decoration-line: line-through;
        color: #303030;
    }
    .completed{
        background-color: #aaa;
    }
    .completed button{
        background-color: #c82727;
        border-color: #9d2a1f;
    }
    .completed button:hover{
        background-color: #910000;
        border-color: #5e0800;
    }
    .todoadditem input{
        width: calc(90% - 30px - 4px);
        padding:15px;
        border-radius: 25px 0;
        border: 2px solid #303030;
        font-size: 18px;
    }
    .todoadditem input:focus{
        box-shadow: 0px 0px 3px 3px #ffffffb5;
        outline:none;
    }
    .todoadditem button{
        width: 90%;
        background-color: #7dc300;
        border: 1px solid #669f00;
        padding: 15px;
        color: #fff;
        border-radius: 25px 0;
        font-size: 18px;
        line-height: 1;
        letter-spacing: 0.1em;
        font-weight: 600;
        margin: 25px 0;
        transition: all 0.5s linear 100ms;
    }
    .todoadditem button:hover{
        background-color: #3b5b00;
        border-color: #142000;
        cursor: pointer;
    }
</style>