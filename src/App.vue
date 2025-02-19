<script setup>
import { ref } from 'vue'
import projectData from './data/projects.json'
import technicalSkillsData from './data/technicalskills.json'

const showProjects = ref(false) // use ref to live update the var for toggling active element

function GoToLink(link) {
  window.open(link, '_blank')
}

function scrollToSection(elementId) {
  const element = document.getElementById(elementId)
  if (element) {
    element.scrollIntoView({behavior: "smooth"})
  }
}
</script>


<template>
  <link rel="stylesheet" type='text/css' href="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/devicon.min.css" />
  
  <!--Main page-->
  <div v-if="!showProjects" class="h-screen w-screen flex items-center justify-center overflow-x-hidden overflow-y-hidden">
    <div class="w-screen h-screen grid grid-cols-2">
      <!-- LEFT SIDE -->
      <div class="text-white p-6 flex flex-col lg:pl-40">
        <h1 class="font-bold lg:text-5xl text-2xl pt-10">Jake Landrum</h1>
        <p class="pt-4 lg:text-xl text-lg font-semibold">Software Engineer</p>

        <div class="mt-10 space-y-4">
          <button @click="scrollToSection('aboutMe')" class="text-gray-400 hover:text-white hover:cursor-pointer">• About Me</button>
          <br>
          <button @click="scrollToSection('projects')" class="text-gray-400 hover:text-white hover:cursor-pointer">• Projects</button>
          <br>
          <button @click="scrollToSection('technicalSkills')" class="text-gray-400 hover:text-white hover:cursor-pointer">• Technical Skills</button>
        </div>

        <div class="mt-auto flex space-x-4 pt-10">
          Contact me: &nbsp;
          <img @click="GoToLink('https://www.linkedin.com/in/jakealandrum/')" src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/linkedin/linkedin-original.svg" class="w-8 h-8 hover:cursor-pointer">
          <i @click="GoToLink('https://github.com/jakeyboi1')" class="devicon-github-original-wordmark hover:cursor-pointer" style="font-size: xx-large;"></i>
          </div>
      </div>

      <!-- RIGHT SIDE -->
      <div class="overflow-y-auto h-screen text-white p-6">
        <!--About me-->
        <h1 id="aboutMe" class="text-2xl font-medium text-center pt-10">About Me</h1>
        <p class="pt-6 lg:text-lg text-gray-400 opacity-95">
          I’m a software engineer passionate about creating high-quality, efficient systems that prioritize well-written code and optimal performance. Problem-solving is at the core of my approach, and I strive to build impactful, optimal, and well-documented solutions.
          <br /><br />
          Currently, I’m pursuing an Associate’s Degree in Computer Programming, with a focus on practical experience and keeping up-to-date with the latest technologies and industry trends. Through both academic and personal projects, I am continually refining my technical skills.
          <br /><br />
          In my free time, I enjoy playing video games, watching horror movies, and keeping myself occupied with hobby coding projects!
        </p>

        <!--Projects-->
        <h1 id="projects" class="text-2xl font-medium text-center pt-20 pb-10">My Projects</h1>
        <div class="grid grid-rows-4 lg:gap-4 mt-4">
          <div v-for="project in projectData">
            <div v-if="project.isShowcase" @click="GoToLink(project.projectLink)" class="hover:opacity-70 hover:cursor-pointer">
              <h1 class="text-lg font-semibold flex">
                {{ project.projectName }}
                <svg class="w-4 ml-2" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 25 25"><path style="fill:#FFFFFF" d="m17.5 5.999-.707.707 5.293 5.293H1v1h21.086l-5.294 5.295.707.707L24 12.499l-6.5-6.5z" data-name="Right"/></svg>
              </h1>
              <p class="text-gray-400 opacity-95 pt-2 pb-2">
                {{ project.description }}
              </p>
              <button v-for="lang in project.languagesUsed" class="bg-gray-700 ml-1.5 text-white font-bold px-1 rounded-full text-sm hover:cursor-pointer ">
                {{ lang }}
              </button>
              <br>
            </div>
          </div>
          <button class="pt-4 text-left font-bold hover:opacity-80 hover:cursor-pointer flex" @click="showProjects = true">
            View All Projects
            <svg class="w-4 ml-2" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 25 25"><path style="fill:#FFFFFF" d="m17.5 5.999-.707.707 5.293 5.293H1v1h21.086l-5.294 5.295.707.707L24 12.499l-6.5-6.5z" data-name="Right"/></svg>
          </button> 
        </div>

        <!--Programming Languages/Technologies-->
        <h1 id="technicalSkills" class="text-2xl font-medium text-center pt-20 pb-10">
          Technical Skills
        </h1>
        <div class="grid lg:grid-cols-4 grid-rows-4 lg:gap-4 mt-4">
          <div v-for="skill in technicalSkillsData">
            <img :src="skill.imgLink" :alt="skill.name" class="h-20 w-20"/>
            <!--https://devicon.dev/ this is the website for the icons for future reference-->
          </div>
        </div>
      </div>
    </div>
  </div>

  <!--All Projects Page-->
  <!--I could use Vue Router for this and actually make different pages but considering I only have 2 its just not needed the ref var works fine-->
  <div v-if="showProjects" class="h-screen w-screen overflow-x-hidden">
    <div class="w-full h-full">
      <button @click="showProjects = false" class="flex text-lg pt-2 pl-2 text-gray-400 hover:text-white hover:cursor-pointer">
        <svg class="w-4 ml-2" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 25 25"><path style="fill:#FFFFFF" d="M24 12.001H2.914l5.294-5.295-.707-.707L1 12.501l6.5 6.5.707-.707-5.293-5.293H24v-1z" data-name="Left"/></svg>
        Return Home
      </button>
      <h1 class="align-top text-white font-bold lg:text-5xl text-2xl pt-10 pb-14 text-center">
        All Projects
      </h1>
      <table class="table-fixed w-full h-60 text-center">
        <thead class="align-top text-white font-bold border-b-2 border-gray-600 text-lg">
          <tr>
            <th>Year</th>
            <th>Name</th>
            <th>Made With</th>
            <th>Link</th>
          </tr>
        </thead>
        <tbody v-for="project in projectData" class="text-white border-b-2 border-gray-600">
          <tr>
            <td class="opacity-80">{{ project.yearMade }}</td>
            <td class="font-semibold">{{ project.projectName }}</td>
            <td>
              <table class="table-fixed mx-auto">
                <td v-for="lang in project.languagesUsed" class="pl-2 opacity-80">{{ lang }}</td>
              </table>
            </td>
            <td class="text-gray-400 hover:text-white hover:opacity-80 hover:cursor-pointer">{{ project.projectLink }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<style scoped>
</style>

<!-- TODO
- Do a mobile design, instead of making the one desgin attempt to look ok on mobile make 2 designs one for mobile one for pc
- Add a resume download/view button
-->