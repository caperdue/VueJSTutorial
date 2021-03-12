<template>
  <div id="app">
    <h2>VueJS Experiment by  {{ myInfo.name }}</h2>
    <h2>Personal Info</h2>
    Name: {{myInfo.name}}
    Semester: {{myInfo.semester}} {{myInfo.year}}<br/>
    Courses I am taking
    <ol>
      <li v-for="(c, pos) in myInfo.courses" :key="pos">
        {{c.name}} ({{c.credits}} credits)</li>
    </ol>    

    <img alt="Vue logo" src="./assets/logo.png">
    <!--<hello-world msg="Welcome to Your Vue.js + TypeScript App"/>-->
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator';
import HelloWorld from './components/HelloWorld.vue';

@Component({
  components: {
    HelloWorld,
  },
})
export default class App extends Vue {
  readonly me = "Carly"
  readonly myInfo = {
    name: "Carly",
    semester: "Winter",
    year: 2021,
    courses: [
      {name: "CIS 263 Data Structures and Algorithms", credits: 3},
      {name: "CIS 371 Web Application Programming", credits: 3},
      {name: "CIS 290 Professional Responsibilities and Practices", credits: 3},
      {name: "MTH 325 Discrete Structures: Computer Science 2", credits: 3},
      {name: "MTH 312 Cryptography and Privacy", credits: 3},
    ],
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
