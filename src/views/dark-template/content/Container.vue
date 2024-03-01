<template>
  <v-card color="grey lighten-4" light>
    <v-card-text>
      <content-section title="Who am I?">
        🚀
        <strong
          >Elevating Digital Experiences: Unleashing Innovation in the Tech Hub
        </strong>
        🌐 <br /><br />
        Hey there! I'm a seasoned full-stack developer with a passion for
        crafting cutting-edge web applications. With over 6 years of expertise,
        I thrive in the dynamic world of modern web development.
        <br />
        <br />
        🛠️ <strong>Tech Arsenal</strong>: Specializing in Vue.js, TypeScript,
        and JavaScript for front-end wizardry, and wielding the power of Node.js
        for back-end brilliance, I bring a versatile skill set to the
        development table. <br /><br />
        🔥 <strong>Passion Unleashed</strong>
        I'm not just in the business of coding; I'm on a mission to create
        exceptional, reusable, and efficient software solutions. My motivation
        is fueled by a genuine love for building top-notch web applications that
        stand out from the crowd.
        <br /><br />
        🌉 <strong>Tech Odyssey in Californi</strong>
        Navigating the vibrant tech landscape of California, particularly in the
        innovation epicenter of San Francisco, I've worn many hats in small
        startup environments. Working remotely, I've been at the forefront,
        leading the charge in developing features from scratch. It's been an
        exhilarating journey, gaining a wealth of experience while contributing
        to the ever-evolving tech scene.
        <br /><br />
        💡 <strong>Diverse Domains, One Maestro </strong>
        My journey isn't confined to web applications alone. From desktop
        applications to mobile adaptation and the creation of single-page
        wonders, I've dabbled in it all. But wait, there's more! Dive into the
        exciting realm of the Internet of Things (IoT) with me, where practical
        experience meets innovation.
        <br /><br />
        🚀 <strong>Conclusion</strong>
        So, why choose me? I'm not just a developer; I'm a tech enthusiast, an
        innovation catalyst, and a seasoned professional ready to take your
        digital dreams to new heights. Let's code the future together! 💻✨
      </content-section>
      <content-section v-if="prouds" title="What am I proud of?">
        <v-layout v-for="(proud, i) in prouds" :key="i">
          <v-flex md1 xs3>
            <v-icon right>
              {{ proud.icon }}
            </v-icon>
          </v-flex>
          <v-flex md11 xs9>
            <p>
              <strong>{{ proud.text }}</strong
              ><br />
              <small>{{ proud.source }}</small>
            </p>
          </v-flex>
        </v-layout>
      </content-section>
      <content-section v-if="educations" title="Education">
        <v-layout v-for="(education, i) in educations" :key="i">
          <v-flex md4> {{ education.from }} - {{ education.to }} </v-flex>
          <v-flex md8>
            <strong v-if="education.title">{{ education.title }}</strong>
            <div v-if="education.location">
              <a :href="education.link" target="_blank"><i>{{ education.location }}</i></a>
            </div>
            <div v-if="education.description">
              {{ education.description }}
            </div>
          </v-flex>
        </v-layout>
      </content-section>
      <content-section v-if="skills" id="to-timeline" title="Skills">
        <template slot="actions">
          (% are relative not absolute)
        </template>
        <v-layout wrap>
          <template v-for="(skill, i) in skills">
            <v-flex v-if="skill.divider" :key="i" md12 xs12 mb-4 />
            <v-flex v-else :key="i" md6 xs12>
              <div class="mr-2 ml-2">
                <div class="align-center">
                  <v-icon small>
                    {{ skill.icon }}
                  </v-icon>
                  {{ skill.title }}
                </div>
                <v-progress-linear
                  class="progress"
                  color="secondary"
                  height="3"
                  :value="skill.value"
                />
              </div>
            </v-flex>
          </template>
        </v-layout>
      </content-section>
    </v-card-text>
  </v-card>
</template>

<script>
import ContentSection from "@/views/dark-template/content/Section";
export default {
  name: "MainContent",
  components: { ContentSection },
  data: () => ({
    prouds: [
            {
        icon: "mdi-account-multiple",
        text: "Working for over two years in a company dedicated to carbon reduction and environmental sustainability. I am proud to have contributed to the efforts aimed at reducing carbon dioxide emissions from the atmosphere",
        source: "(Twelve)",
      },
      {
        icon: "mdi-help-rhombus-outline",
        text: "I've helped several startup companies accelerate their growth!",
      },
      {
        icon: "mdi-library-music",
        text:
          "I have obtained a certificate for entering the Arctic Circle.",
        source: "(Located at 66º33’)",
      },

    ],
    educations: [
      {
        from: "2015",
        to: "2017",
        title: "Master's degree, Computer Science",
        location: "Illinois Insititute Of Technology",
        link: 'https://www.iit.edu'
      },
      {
        from: "2011",
        to: "2015",
        title: "Bachelor's degree, Software Engineer",
        location: "Nanjing University of Posts and Telecommunications",
        link: 'https://www.njupt.edu.cn/en/'
      },
    ],
    skills: [
      {
        title: "NodeJS",
        icon: "mdi-language-php",
        value: 95,
      },
      {
        title: "JavaScript",
        icon: "mdi-language-javascript",
        value: 95,
      },
            {
        title: "PostgreSQL",
        icon: "mdi-ubuntu",
        value: 90,
      },
            {
        title: "Vue Framework",
        icon: "mdi-vuejs",
        value: 95,
      },
      {
        title: "TypeScript",
        icon: "mdi-language-javascript",
        value: 80,
      },
      {
        title: "React Framework",
        icon: "mdi-laravel",
        value: 80,
      },
        {
        title: "HTML",
        icon: "mdi-laravel",
        value: 95,
      },
       {
        title: "CSS",
        icon: "mdi-laravel",
        value: 95,
      },
             {
        title: "Storybook",
        icon: "mdi-laravel",
        value: 85,
      },
                   {
        title: "Figma",
        icon: "mdi-laravel",
        value: 70,
      },
      { divider: true },
      {
        title: "Graphql",
        icon: "mdi-ubuntu",
        value: 90,
      },
      {
        title: "Ubuntu Server",
        icon: "mdi-ubuntu",
        value: 90,
      },
      {
        title: "Web Application",
        icon: "mdi-shield-lock",
        value: 90,
      },
      {
        title: "Test Driven Development",
        icon: "mdi-test-tube",
        value: 85,
      },
      {
        title: "CI/CD",
        icon: "mdi-truck-fast",
        value: 85,
      },
      {
        title: "AWS",
        icon: "mdi-truck-fast",
        value: 85,
      },
      {
        title: "GCP",
        icon: "mdi-truck-fast",
        value: 70,
      },
      {
        title: "Git",
        icon: "mdi-git",
        value: 95,
      },
      { divider: true },
      {
        title: "Frimware Development",
        icon: "mdi-chip",
        value: 65,
      },
      {
        title: "Golang",
        icon: "mdi-language-cpp",
        value: 65,
      },
      { divider: true },
    ],
  }),
};
</script>

<style scoped>
.title {
  border-bottom: 2px #bfbfbf solid;
  line-height: 1.5 !important;
}
.progress {
  margin-top: 0.1rem;
}
</style>
