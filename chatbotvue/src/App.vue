<template>
  <div id="app">
    <h1 class="site-title"><span class="todo">To</span><span class="todo">Do</span><span class="rest-of-title">list</span></h1>
    <div class="menu-container">
      <div class="options">
        <div class="option" v-for="option in menu" :key="menu[option]" :style="cssVars">
          <a href="option.url">
            <p>{{option.title}}</p>
          </a>
        </div>
      </div>
    </div>
    <div class="content">
      <SideBar />
    </div>
    <div class="footer">
      <p>Wiktor Fajkowski 2022. | All rights reserved &copy;</p>
    </div>
  </div>
</template>

<script>
  import ToDos from "./components/ToDos.vue"
  let menu = [{title: "Strona główna", url: "url"}, {title: "Nowości", url: "url"}, {title: "O nas", url: "url"}]
  export default {
    name: 'App',
    components: {
      SideBar: ToDos
    },
    data() {
      return {
        menu: menu
      }
    },
    computed: {
      cssVars() {
        return {
          '--width': `${(100 / menu.length) - 5}%`
        }
      }
    }
  }
</script>

<style>
  @import url("https://fonts.googleapis.com/css2?family=Roboto&display=swap");

  body{
    margin: 0 !important;
    height: 100% !important;
  }
  #app {
    font-family: 'Roboto', sans-serif;
  }
  .site-title {
    text-align: center;
    text-transform: uppercase;
    margin:30px 0;

  }
  .rest-of-title {
    font-size: 120%;
    padding:0px 15px;
    color: #303030;
  }
  .todo {
    background-color: #303030;
    padding:10px 30px;
    border-top-right-radius:0px;
    border-bottom-right-radius:25px;
    color: #fff;
  }
  .todo:first-child{
    border-top-left-radius:25px;
    border-bottom-left-radius:0px;
    border-top-right-radius:0;
    border-bottom-right-radius:0;
    background-color: #00c300;
    color: #303030;
  }
  .menu-container {
    width:100%;
    height:80px;
    background-color: #303030;
  }
  .option{
    width:var(--width);
    margin:10px 2.5%;
    background-color: #00c300;
    height:60px;
    float:left;
    border-radius:25px 0;
    transition: all 0.5s linear 100ms;
  }
  .options{
    margin:0 auto;
    width:75%;
    text-align:center;
  }
  .option > a > p{
    margin:18px;
    font-size:22px;
  }
  .option > a {
    text-decoration:none;
    color: #303030;
    transition: all 0.5s linear 100ms;
  }
  .option:hover{
    background-color: darkgreen;
  }
  .option:hover > a {
    color: lime;
  }
  .content{
    width: 100%;
    min-height: 700px;
  }
  .footer{
    width: 100%;
    height: 100px;
    background-color: #303030;
    text-align: center;
    font-size: calc(14px + 1vw);
  }
  .footer > p {
    padding:30px 0;
    color: white;
    margin:0;
  }
</style>
