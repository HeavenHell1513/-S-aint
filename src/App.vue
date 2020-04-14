<template>
  <div id="app"  class="Osnova">
    <img alt="Vue logo" src="./assets/logo.png">
      <HelloWorld msg="Welcome to Your Vue.js App"/>
<!--      Первая страница-->
<!--      <div v-if="easy">-->
     <br>
      <a class="Knopka">
      <input v-model="Line" type="text" placeholder="Text" v-on:keyup.enter="RespTop">
      <input type="submit" value="Send" @click="RespTop">
    </a>
      <br>
    <ul type="none" align="left">
      <li v-for="(man,index) in HeroTop" :key="man.message">
        <input  type="checkbox" v-model="man.Zakup">
<!--          <span :style="{'text-decoration': man.Zakup==1?'line-through':'none'}">{{index + 1}} - {{man.message}}</span>-->
          <span :class="{'del': man.Zakup}">{{index + 1}}. {{man.message}}</span>
        <button  @click="NukeTop(index)" align="right">Delete</button >
<!--          <del v-if="man.Zakup">{{index + 1}} - {{man.message}}</del>-->
<!--          <span v-else>{{index + 1}} - {{man.message}}</span>-->
      </li>
    </ul>
<!--      <br>-->
      <input type="button" value="Выделить все" @click="TeamTop">
      <input type="button" value="Удалить выделенное" @click="KillTop">
      <br>
<!--      </div>-->
<!--      Вторая страница-->
<!--      <div v-if="!easy">-->
<!--          <a><br>-->
<!--              <input v-model="Line" type="text" align="center" placeholder="Text" v-on:keyup.enter="RespBot">-->
<!--              <input type="submit" value="Send" @click="RespBot">-->
<!--          </a>-->
<!--          <ul type="none">-->
<!--              <li v-for="(man,index) in HeroBot" :key="man.message">-->
<!--                  <input  type="checkbox" v-model="man.Zakup">-->
<!--                  &lt;!&ndash;          <span :style="{'text-decoration': man.Zakup==1?'line-through':'none'}">{{index + 1}} - {{man.message}}</span>&ndash;&gt;-->
<!--                  <span :class="{'del': man.Zakup}">{{index + 1}}. {{man.message}}</span>-->
<!--                  <button  @click="NukeBot(index)">Delete</button >-->
<!--                  &lt;!&ndash;          <del v-if="man.Zakup">{{index + 1}} - {{man.message}}</del>&ndash;&gt;-->
<!--                  &lt;!&ndash;          <span v-else>{{index + 1}} - {{man.message}}</span>&ndash;&gt;-->
<!--              </li>-->
<!--          </ul>-->
<!--          &lt;!&ndash;      <br>&ndash;&gt;-->
<!--          <input type="button" value="Выделить все" @click="TeamBot">-->
<!--          <input type="button" value="Удалить выделенное" @click="KillBot">-->
<!--          <br>-->
<!--      </div>-->
<!--      <input type="submit" value="Top" @click="Top"> &nbsp;-->
<!--      <input type="submit" value="Bot" @click="Bot">-->
  </div>
</template>

<script>
  // import HelloWorld from './components/HelloWorld.vue'

  export default {
    name: 'App',
    components: {
// HelloWorld
    },
    data(){
      return{
          Line:"",
          Che:0,
          i:1,
          easy:true,
// name2:"punkt 2",
        HeroTop:[
          {id:2, message: 'Traxes', Zakup:1 },
          {id:1, message: 'Lina', Zakup:0}
        ],
          // HeroBot:[
          //     {id:3, message: 'Axe', Zakup:0 },
          //     {id:1, message: 'Sniper', Zakup:1}
          // ]

      }
    },
    methods:{
      Gang({target}){
        console.log(target.value)
      },
      RespTop(){
          this.HeroTop.push({id:Date.now(), message: this.Line, Zakup:0});
          this.Line=null;},
        RespBot(){
            this.HeroBot.push({id:Date.now(), message: this.Line, Zakup:0});
            this.Line=null;},
      KillTop(){
          for (var i=0;i<this.HeroTop.length;++i){
              if(this.HeroTop[i].Zakup==1){
                  this.HeroTop.splice(i,1);
                  i=i-1;}}
            },
        // KillBot(){
        //     for (var i=0;i<this.HeroBot.length;++i){
        //         if(this.HeroBot[i].Zakup==1){
        //             this.HeroBot.splice(i,1);
        //             i=i-1;}}
        // },
      TeamTop(Che,i){
          Che=1;
          for (i=0;i<this.HeroTop.length;++i){
              if (this.HeroTop[i].Zakup == 0)
                  Che=0
          }
          for (i=0;i<this.HeroTop.length;++i){
              if (Che==1)
                  this.HeroTop[i].Zakup=0;
              else
                this.HeroTop[i].Zakup=1
          }
      },
        // TeamBot(Che,i){
        //     Che=1;
        //     for (i=0;i<this.HeroBot.length;++i){
        //         if (this.HeroBot[i].Zakup == 0)
        //             Che=0
        //     }
        //     for (i=0;i<this.HeroBot.length;++i){
        //         if (Che==1)
        //             this.HeroBot[i].Zakup=0;
        //         else
        //             this.HeroBot[i].Zakup=1
        //     }
        // },
      NukeTop(index){
        this.HeroTop.splice(index,1)
      },
      //   NukeBot(index){
      //       this.HeroBot.splice(index,1)
      //   },
      //   Top(){
      //       this.easy = true;
      //   },
      //   Bot() {
      //       this.easy = false;
      //   }
    }
  }
</script>

<style>
  body{
      background-color: aqua;
  }
    #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
  .del {
        text-decoration: line-through;
    }
    .Osnova{
        background-color: grey;
        width: 800px;
        margin-left: 15vw;
    }
    .Knopka{
        float:left;
    }
</style>