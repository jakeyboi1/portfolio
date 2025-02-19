<script setup>
import projectData from './data/projects.json'
import technicalSkillsData from './data/technicalskills.json'

function GoToLink(link) {
  window.open(link, '_blank')
}

function scrollToSection(elementId) {
  const element = document.getElementById(elementId);
  if (element) {
    element.scrollIntoView({behavior: "smooth"});
  }
}
</script>


<template>
  <link rel="stylesheet" type='text/css' href="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/devicon.min.css" />
  
  <div class="h-screen w-screen flex items-center justify-center overflow-x-hidden overflow-y-hidden">
    <div class="w-screen h-screen border border-gray-700 grid grid-cols-2">
      <!-- LEFT SIDE -->
      <div class="border-r border-gray-700 text-white p-6 flex flex-col lg:pl-40">
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
          <img @click="GoToLink('https://www.linkedin.com/in/jakealandrum/')" src="https://img.icons8.com/?size=100&id=8808&format=png&color=737373" class="w-8 h-8 hover:cursor-pointer">
          <img @click="GoToLink('https://github.com/jakeyboi1')" src="https://img.icons8.com/?size=100&id=RHLuYrY4GjUv&format=png&color=737373" class="w-8 h-8 hover:cursor-pointer">
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
          <button class="pt-4 text-left font-bold hover:opacity-80 hover:cursor-pointer flex">
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
</template>

<style scoped>
</style>