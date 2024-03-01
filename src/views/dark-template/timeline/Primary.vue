<template>
  <v-card
    color="grey lighten-4"
    light
  >
    <v-card-text>
      <content-section
        id="timeline"
        :title="detailed ? 'My Life in a Nutshell' : 'My Experiences'"
      >
        <template slot="actions">
          <div>
            <v-switch
              v-model="detailed"
              :label="detailed ? 'Detailed' : 'Summary'"
            />
          </div>
        </template>

        <v-timeline
          dense
        >
          <v-timeline-item
            v-for="(item, i) in orderedItems"
            :key="i"
            :icon="item.icon || ''"
            :class="{transparent: item.transparent}"
            large
          >
            <template
              v-if="item.iconImage"
              v-slot:icon
            >
              <v-avatar>
                <img
                  :src="publicPath(item.iconImage)"
                >
              </v-avatar>
            </template>
            <template v-slot:opposite />
            <v-layout>
              <v-flex
                v-if="$vuetify.breakpoint.smAndUp"
                md1
                sm2
                align-self-center
              >
                <span>{{ item.year }}</span>
              </v-flex>
              <v-flex
                md11
                sm10
                xs12
              >
                <v-card class="elevation-1">
                  <v-card-title class="pb-0">
                    <div>
                      <p v-if="$vuetify.breakpoint.xsOnly">
                        {{ item.year }}
                      </p>
                      <h3>{{ item.title }}</h3>
                    </div>
                  </v-card-title>
                  <v-card-text>
                    <v-layout wrap>
                      <v-flex
                        :md7="!!item.image"
                        :md12="!item.image"
                        xs12
                      >
                        <div class="mr-1">
                          <span
                            v-if="item.text"
                            class="pre"
                          >{{ item.text }}</span>
                          <!-- eslint-disable vue/no-v-html -->
                          <div
                            v-else-if="item.html"
                            v-html="item.html"
                          />
                          <!-- eslint-enable vue/no-v-html -->
                        </div>
                      </v-flex>
                      <v-flex
                        v-if="item.image"
                        md5
                        xs12
                      >
                        <div
                          class="mt-2"
                        >
                          <v-carousel
                            v-if="Array.isArray(item.image)"
                            :show-arrows="false"
                            :height="325"
                          >
                            <v-carousel-item
                              v-for="(citem,ci) in item.image"
                              :key="ci"
                              :src="publicPath(citem)"
                            />
                          </v-carousel>
                          <v-img
                            v-else
                            :max-height="item.imageHeight ? item.imageHeight : ''"
                            :src="publicPath(item.image)"
                          />
                        </div>
                      </v-flex>
                    </v-layout>
                  </v-card-text>
                </v-card>
              </v-flex>
            </v-layout>
          </v-timeline-item>
        </v-timeline>
      </content-section>
    </v-card-text>
  </v-card>
</template>

<script>
import ContentSection from '@/views/dark-template/content/Section'
export default {
  name      : 'Timeline',
  components: { ContentSection },
  data      : () => ({
    detailed: true,
    items   : [
      {
        year       : '2015 Aug',
        transparent: true,
        title      : `Embark on my journey to pursue a Master's Degree in the United States.`,
      },
      {
        year : 'Jan 2017 ',
        title: 'Secure a Software Engineer Internship at MacDonald Software',
        html : `
        <ul>
  <li>Develop a Cloud-based dashboard with IoT devices for viewing, monitoring, filtering, alerting, and analyzing data.</li>
  <li>Implement user access control settings for dashboard and features at various levels.</li>
  <li>Create a Machine Setting Dashboard inside Linux-based IoT Machines with data streaming through AWS Lambda Gateway.</li>
  <li>Also learned extensively about McDonald's Food POS system, Drive-through system, Mobile Order, Dine-in system, and Kiosk.</li>
  <li>Designed test cases, fixed unexpected defects on Kiosk, IOS Mobile App, POS with agile teamwork through JIRA and Kanban Board.</li>
  <li>Designed and implemented Selenium test plans, command-line scripts, deployed new application versions, and tested environments.</li>
</ul>
        `,
      },
      {
        year : 'Dec 2017 ',
        title: 'Get my Master degree in Computer Science',
      },
      {
        year : 'April 2018',
        title: 'Start first full stack developer Job in IOT startup company',
        html : `
          <p>
             <a href="https://www.twelve.co/" target="_blank" > Dynapar </a> - Unicorn in Climate change: <span class="light-blue--text lighten-3"></span><br>
          </p>
  <ul>
  <li>Develop a Cloud-based dashboard with IoT devices for viewing, monitoring, filtering, alerting, and analyzing data.</li>
  <li>Implement user access control settings for dashboard and features at various levels.</li>
  <li>Create a Machine Setting Dashboard inside Linux-based IoT Machines with data streaming through AWS Lambda Gateway.</li>
</ul>
        `,
        image    : 'img/timeline/dynapar.png',
        iconImage: 'img/timeline/dynapar1.png',
      },
      {
        year : '2019',
        title: 'Full Stack Developer',
        html : `
        <p>
              BV USA - A e-commerce company: <span class="light-blue--text lighten-3"></span><br>
          </p>
          <p>Pioneering the role of a Founding Full Stack Engineer in a vibrant e-commerce enterprise based in Chicago. Driving innovation, shaping digital landscapes, and achieving milestones in the dynamic world of technology and commerce</p>
          <p>Contributed to the realization of automated advertising, shipping management, inventory control, and invoice management, streamlining processes and enhancing efficiency across the board</p>
        `,
        iconImage: 'img/timeline/bv_logo.png',
      },
      {
        year : '2021',
        title: 'Join Spot AI',
        html : `
<a href="https://www.spot.ai/" target="_blank" > Spot AI </a>  - Video Intelligence Software
<ul>
  <li>Spearheaded the development of a Dashboard outage notice feature, enabling control and monitoring of edge computer health and performance.</li>
  <li>Innovatively designed and implemented a Connect/Cast Troubleshooting web tool for client-end kiosks, including Smart TVs, PCs, and mobile phones.</li>
  <li>Architected and constructed connections on Docker containers and Cloudflare tunnels, facilitating seamless communication between the dashboard, API, Cloudflare, and IoT devices to enhance hardware product accessibility.</li>
  <li>Implemented robust user access control, device settings, and configuration for locations and cameras on both the Dashboard and IoT devices.</li>
  <li>Contributed to the enhancement of the Video Player dashboard with the development of additional features, optimization of web pages for mobile devices, and improvements in video streaming quality.</li>
  <li>Designed and implemented...</li>
</ul>

        `,
        image    : 'img/timeline/spot_image.png',
        iconImage: 'img/timeline/spot.png',
      },
      {
        year : '2022',
        title: 'Full Stack developer',
        html : `
          <p>
             <a href="https://www.twelve.co/" target="_blank" > Twelve </a> - Unicorn in Climate change: <span class="light-blue--text lighten-3"></span><br>
          </p>
          <ul>
  <li>Orchestrated collaborative initiatives with designers and stakeholders, resulting in the successful delivery of numerous cutting-edge features and receiving positive feedback.</li>
  <li>Achieved substantial time savings and error reduction through the implementation of essential, efficient, and reusable components.</li>
  <li>Led the development of pivotal features in the web platform as a full-stack engineer, enhancing data visualization and optimizing operations records.</li>
  <li>Pioneered innovative solutions to boost the scalability and performance of cloud-based data platforms, ensuring seamless integration with state-of-the-art technologies, machines, and hardware in the climate change industry.</li>
  <li>Designed and developed a variety of reusable components, including checklists, customizable input fields, and controllable layouts, demonstrating a commitment to efficiency and maintainability.</li>
  <li>Maintained optimal web platform performance through continuous monitoring and analysis, identifying areas for improvement and implementing solutions to enhance speed, efficiency, and overall user satisfaction.</li>
</ul>
        `,
        image    : 'img/timeline/twelve.png',
        iconImage: 'img/timeline/twelve_logo.png',
      },
      {
        year : 'So far ...',
        title: 'Looking for new oppotinuties',
        html : `I am currently seeking new opportunities and challenges, eager to delve into continuous learning, and elevate my technical skills and capabilities. I am in search of a broader platform where I can optimize my potential and contribute positively. Embracing a mindset of continuous growth, I am excited about the prospect of expanding my horizons and achieving new milestones in my professional journey.`,
        icon: 'mdi-fountain-pen-tip',
      },
    ],
  }),
  computed: {
    orderedItems () {
      const items = [...this.items].reverse()
      if (this.detailed)
        return items
      return items.filter((item) => {
        return !item.detailed
      })
    },
  },
}
</script>

<style scoped>
.title {
  border-bottom: 2px #bfbfbf solid;
  line-height: 1.5 !important;
}
.pre {
  white-space: pre;
}
.transparent{
  opacity: 0.6;
}
</style>
