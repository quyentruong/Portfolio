<template>
  <div>
    <v-row v-for="i in Math.ceil(projects.length/projectPerRow())" :key="i*1.083">
      <v-col v-for="j in projectPerRow()" :key="j*3.083">
        <v-card
          v-if="indexComputed(i,j) < projects.length"
          max-width="500"
          class="mx-auto"
        >
          <v-list-item>
            <v-list-item-avatar v-if="project(i,j).avatar.length > 0" color="white">
              <img
                v-lazy-load
                :data-src="require(`../assets/avatar/${project(i,j).avatar}`)"
              >
            </v-list-item-avatar>
            <v-list-item-content>
              <v-list-item-title class="headline">
                {{ project(i,j).title }}
              </v-list-item-title>
              <v-list-item-subtitle>{{ project(i,j).subtitle }}</v-list-item-subtitle>
              <v-list-item-subtitle>{{ project(i,j).subtitle2 }}</v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>

          <img
            v-if="project(i,j).frontpage"
            v-lazy-load
            :data-src="require(`../assets/frontpage/${project(i,j).frontpage}`)"
            height="194"
            width="500"
            :alt="project(i,j).frontpage"
          >

          <v-card-text>
            {{ project(i,j).text }}
          </v-card-text>

          <v-card-actions>
            <v-btn
              v-if="project(i,j).link && typeof (project(i,j).link) === 'string'"
              text
              color="deep-purple accent-4"
              :href="project(i,j).link"
              target="_blank"
            >
              Link
            </v-btn>
            <v-menu v-else>
              <template v-slot:activator="{ on }">
                <v-btn
                  text
                  color="deep-purple accent-4"
                  v-on="on"
                >
                  Links
                </v-btn>
              </template>
              <v-list>
                <v-list-item v-for="link in project(i,j).link" :key="link+i*j*2.034">
                  <v-btn
                    text
                    :href="link"
                    target="_blank"
                  >
                    {{ link }}
                  </v-btn>
                </v-list-item>
              </v-list>
            </v-menu>
            <v-spacer />
            <Showcase v-if="project(i,j).showcase" :folder="project(i,j).showcase" />
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </div>
</template>

<script>

import { routerOptions } from '../.nuxt/router'
import Showcase from './Showcase'
// const cache = {}
// const images = require.context('../static/showcase/mudbay/', false, /\.png$/)
// const imagesArray = Array.from(images.keys())
// const constructed = []
// function constructItems (fileNames, constructed) {
//   fileNames.forEach((fileName) => {
//     constructed.push({
//       src: fileName.substr(1)
//     })
//   })
//   return constructed
// }
// const res = constructItems(imagesArray, constructed)
// console.log(res)
export default {
  name: 'Project',
  components: { Showcase },
  data: () => ({
    projectPerRow () {
      switch (this.$vuetify.breakpoint.name) {
        case 'xs':
          return 1
        case 'sm':
          return 2
        default:
          return 3
      }
    },
    projects: [
      {
        avatar: 'mudbay.png',
        frontpage: 'mudbay.png',
        title: 'Mudbay',
        subtitle: 'PHP, Vue',
        subtitle2: 'WordPress',
        text: 'Create PHP API to cache data from SmartSheet to MySQL. Create four pages: ‘stores’, ‘store’, ‘events’, ‘brands’ by using Vue. Then implement these pages to existing WordPress. Built data driven templates that read data from smartsheets. Also mention that you built an integration with smartsheets that used custom built caching.',
        link: ['http://mudbay.com/', 'https://www.mudbay.com/stores/', 'https://www.mudbay.com/events/', 'https://www.mudbay.com/cat-brands-we-carry/', 'https://www.mudbay.com/dog-brands-we-carry/'],
        showcase: 'mudbay'
      },
      {
        avatar: 'activ.png',
        frontpage: 'activ.jpg',
        title: 'ACTiV',
        subtitle: 'C#, HTML, JavaScript, CSS',
        subtitle2: 'MVC Net Core, BootStrap 4',
        text: 'Migrate webforms template to MVC pattern. Implement Entity Framework for SQL. Implement Azure Ad Directory for Authentication. Implement DataTables.net for administration (View, Delete, Print, Add Comment). Implement OneClick to send email to users by using Azure Logic App.',
        link: 'http://www.goactiv.org/',
        showcase: 'activ'
      },
      {
        avatar: 'connectmyvariant.png',
        frontpage: 'connectmyvariant.png',
        title: 'ConnectMyVariant',
        subtitle: 'PHP, HTML, JavaScript, CSS, MySQL',
        subtitle2: 'Laravel, NuxtJs, Vuetify',
        text: 'Designed relational database. Used Laravel’s migration tool to create tables. Implemented API in Laravel to allow database functionality (read, create, delete). Implemented Nuxt SPA to create datatable and migrated it to existing Laravel project. Created HTML datatable to improve Search Engine Optimization (SEO). Created a NodeJS script to generate sitemap. Submitted final project to Google Search Console to improve SEO.',
        link: 'http://connectmyvariant.org/'
      },
      {
        avatar: '',
        frontpage: 'populationss.png',
        title: 'Population Screening Study',
        subtitle: 'C#, HTML, JavaScript, CSS',
        subtitle2: 'MVC Net Core, BootStrap 4',
        text: 'Created .Net Core MVC Website. Implemented Entity Framework for SQL and created Administration Management page to allow moderators to add participant results. Designed the website to send emails to participants via a link with a generated ID for participants to allow them check their status.',
        link: 'https://docker331.herokuapp.com/Home/'
      },
      {
        avatar: '',
        frontpage: 'fisherman.jpg',
        title: 'Fishermen',
        subtitle: 'C#, HTML, JavaScript, CSS, SQL',
        subtitle2: 'NuxtJS, API NetCore, Vuetify',
        text: 'Created Front End Vue framework. Then connect to .Net Core WebAPI to get data. Graph the best month to fish. Graph best place to fish. Write Custom Query to do filter and sort any column.',
        link: 'https://fishermen.azurewebsites.net/'
      },
      {
        avatar: '',
        frontpage: 'informationgather.jpg',
        title: 'Information Gather',
        subtitle: 'C#',
        subtitle2: 'Xamarin Android',
        text: "Create an Android app that collect users' information. The app can generate multiple forms then writes to csv on internal storage. It supports function to send email and local authentication to make sure no one use your app without your permission.",
        link: 'https://photos.app.goo.gl/uSErTi7Ycc3ogJDc7',
        showcase: 'informationgather'
      }
    ]
  }),
  methods: {
    indexComputed (i, j) {
      return (j - 1) + (i - 1) * this.projectPerRow()
    },
    project (i, j) {
      return this.projects[this.indexComputed(i, j)]
    },
    hostname () {
      return routerOptions.base
    },
    getImage (path) {
      return require(path)
    }
  }
}
</script>

<style scoped>

</style>
