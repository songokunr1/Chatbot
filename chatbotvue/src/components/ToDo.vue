<template>
    <div id="todoapp">
        <div class="todoitems">
            <div class="todoitem" v-for="item in list.content" :key="item.id">
                <h1 class="todoitem-title">
                    {{item.title}}
                </h1>
                <button class="done">Zrobione!</button>
            </div>
        </div>
        <div class="todoadditem"></div>
    </div>
</template>

<script>
    export default {
        props: ['list'],
        data() {
            return {

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
        border: #142000;
        cursor: pointer;
    }
</style>