<template>
  <div id="app">
    <h2>VueJS Experiment by {{ myInfo.name }}</h2>
    <h2>Personal Info</h2>
    Name: {{ myInfo.name }} Semester: {{ myInfo.semester }} {{ myInfo.year
    }}<br />
    Courses I am taking
    <ol>
      <li v-for="(c, pos) in myInfo.courses" :key="pos">
        {{ c.name }} ({{ c.credits }} credits)
      </li>
    </ol>
    <table>
      <thead>
        <th>Course</th>
        <th>Credits</th>
      </thead>
      <tbody>
        <tr v-for="(c, pos) in myInfo.courses" :key="pos">
          <td>{{ c.name }}</td>
          <td>{{ c.credits }}</td>
        </tr>
      </tbody>
    </table>
    <CourseCard
      v-for="(c, pos) in myInfo.courses"
      :key="pos"
      v-bind:name="c.name"
      v-bind:num-credits="c.credits"
      v-bind:meetings="c.meetings">
    </CourseCard>
    <!--<hello-world msg="Wellcome to Your Vue.js + TypeScript App"/>-->
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import HelloWorld from "./components/HelloWorld.vue";
import CourseCard from "./components/CourseCard.vue";

@Component({
  components: {
    HelloWorld,
    CourseCard,
  },
})
export default class App extends Vue {
  readonly myInfo = {
    name: "Carly",
    semester: "Winter",
    year: 2021,
    courses: [
      {
        name: "CIS 263 Data Structures and Algorithms",
        credits: 3,
        meetings: ["Mon 8-9a", "Fri 8-9a"],
      },
      { 
        name: "CIS 371 Web Application Programming", 
        credits: 3,
        meetings: ["Mon 2-3p", "Wed 2-3p", "Fri 2-3p"],
      },

      {
        name: "CIS 290 Professional Responsibilities and Practices",
        credits: 3,
        meetings: ["Thu 10-11:15p"]
      },
      { 
        name: "MTH 325 Discrete Structures: Computer Science 2", 
        credits: 3,
        meetings: ["Mon 10-11a"]
        },
      { name: "MTH 312 Cryptography and Privacy", 
        credits: 3,
        meetings: ["Mon 12-1p","Wed 12-1p", "Fri 12-1p"]
       },
    ],
  };
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}

table,
tr,
td,
th {
  border: 1px solid black;
}

td:nth-of-type(2) {
  text-align: center;
}
</style>
