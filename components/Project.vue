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
            <v-list-item-avatar v-if="project(i,j).avatar" color="white">
              <v-img
                :src="hostname() + project(i,j).avatar"
              />
            </v-list-item-avatar>
            <v-list-item-content>
              <v-list-item-title class="headline">
                {{ project(i,j).title }}
              </v-list-item-title>
              <v-list-item-subtitle>{{ project(i,j).subtitle }}</v-list-item-subtitle>
              <v-list-item-subtitle>{{ project(i,j).subtitle2 }}</v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>

          <v-img
            v-if="project(i,j).frontpage"
            :src="hostname() + project(i,j).frontpage"
            height="194"
          />

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
            <Showcase v-if="project(i,j).showcase" :images="project(i,j).showcase" />
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </div>
</template>

<script>

import { routerOptions } from '../.nuxt/router'
import Showcase from './Showcase'

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
        avatar: 'avatar/mudbay.png',
        frontpage: 'frontpage/mudbay.png',
        title: 'Mudbay',
        subtitle: 'PHP, Vue',
        subtitle2: 'WordPress',
        text: 'Create PHP API to cache data from SmartSheet to MySQL. Create four pages: ‘stores’, ‘store’, ‘events’, ‘brands’ by using Vue. Then implement these pages to existing WordPress. Built data driven templates that read data from smartsheets. Also mention that you built an integration with smartsheets that used custom built caching.',
        link: ['http://mudbay.com/', 'https://www.mudbay.com/stores/', 'https://www.mudbay.com/events/', 'https://www.mudbay.com/cat-brands-we-carry/', 'https://www.mudbay.com/dog-brands-we-carry/'],
        showcase: ['https://lh3.googleusercontent.com/QBYOkT7FVmKkhkk8BGEYkH3y0BMap50QcUG6H-YAwmDWTVl1ZF4mYKfVmX29dUb_8dB_ujfWAi2d6_DNRVIKhNfpexXOKn-zkG54q6EvYwtlwVqvwFVFwkr3yPsi8pJhPZT4QHuCIpErqlwXYOD88B9L9Pn4GSSPx4_zk3pp_71C1Hqjo8cb3zjOXtZ5F0wFvBvfk7BfhcZSQzwZiW9tr3eNh3zWyyxsy3CfhrTkHEhLG5o4fbk13J9hb4laNkc11939sEOZslBj_e1hsanlcHMHtObVcJ1oF056HDxdhe15RDiCXYof_1Hs8jeyQ9opgeyIvg604V9D-NUqTs0EraGiwhY0X2-s1DxWqU3zxBGpkb7DDTvCNzap3rv7fLUWcYez0DviNij7g0xteineUHNPdVT3410isEWKEL-zXj4_pPXjeyd6lKeGTn936XCgY8eWXVaAN2u8Wwt_BXPzxKi3UKSAo9B4TQr7-N-sKXOKpbB269kqx7RbebOuQ0j7AQg39Pz5EZeqg_XDeME_EJunFKj7HqyP_Z0OA-9HWDiGhMdU2ewqImKruNyResqWmA8i1oFwRW9dNbRSqnpQ-8RAGo_KpCFrJDnR6R4PEmXvYZgHea3ItE1W_CYsMnx8uHQUKPTMkDiw5HrJRobOAMYHBML0z551rVW_EsGFn0UTXTfaPkLKAlDtgm7z=w931-h945-no',
          'https://lh3.googleusercontent.com/WyBiaBEksChHr5bM-Lv_eizdHhSTX0lD0Zm6yY_V_X2WdLsEkt-pk3Q3BTO-J0HsPVAlWt5tHtIWfa0E7dC6QNUYejSIM3v72GER6tqrbAOfYTtJfT74IAuIp6nauyX527LA89YJN8toGZO5qeAkde3zb-nX5uzU2AwsiLYgfSOtlru34CLRmFwQYgzgPJWsT533fmOCB6Lwf0Wv8dCQvSSjbmvqiIjKbpQFuOlW4Iv1iY36umm1ajF5k4Yt-rI86xcf0D5D49waau_4arAKPMDebAxTDV1nFR_NgnxJlYY9zPPlOcOtEXgdOIq_5QQ_THtoYR7ssm1JFpOV6zcSJkBxPkTlFlQH4opgZ_flOpEyhXf0nSnPsVMLK5iLd1Z_QB-nk8GWvwRHpQ_dGmwmRglB6nV3pedNXdzEO2s5ev9WKawQAI8q9_p4pUb48_16sgGMCPEvzMo1TJuWE92O8RjCl3t1QVi2dugxt0KdXZsgqGYG6bFcliSDAzdEYDQPGm-_BTzZcyOnMhJK8jTxvTjaxysTZVkWd7Me9PKcb3Mui8QwINIaMA8qYdkHpue4APi_ZNMvNiRs8hWWFNtG_2zcKLFJULJAAVfFmH4EWH73tz3m09DT6Fi2DYccwwoXWwcfYRlGmZLKNv1s09b8gtJDnP0N807X7ULfgWuW1mSkRDe08tg12CoPuTCA=w851-h944-no']
      },
      {
        avatar: 'avatar/activ.ico',
        frontpage: 'frontpage/activ.jpg',
        title: 'ACTiV',
        subtitle: 'C#, HTML, JavaScript, CSS',
        subtitle2: 'MVC Net Core, BootStrap 4',
        text: 'Migrate webforms template to MVC pattern. Implement Entity Framework for SQL. Implement Azure Ad Directory for Authentication. Implement DataTables.net for administration (View, Delete, Print, Add Comment). Implement OneClick to send email to users by using Azure Logic App.',
        link: 'http://www.goactiv.org/'
      },
      {
        avatar: 'avatar/connectmyvariant.ico',
        frontpage: 'frontpage/connectmyvariant.png',
        title: 'ConnectMyVariant',
        subtitle: 'PHP, HTML, JavaScript, CSS, MySQL',
        subtitle2: 'Laravel, NuxtJs, Vuetify',
        text: 'Designed relational database. Used Laravel’s migration tool to create tables. Implemented API in Laravel to allow database functionality (read, create, delete). Implemented Nuxt SPA to create datatable and migrated it to existing Laravel project. Created HTML datatable to improve Search Engine Optimization (SEO). Created a NodeJS script to generate sitemap. Submitted final project to Google Search Console to improve SEO.',
        link: 'http://connectmyvariant.org/'
      },
      {
        avatar: '',
        frontpage: 'frontpage/populationss.png',
        title: 'Population Screening Study',
        subtitle: 'C#, HTML, JavaScript, CSS',
        subtitle2: 'MVC Net Core, BootStrap 4',
        text: 'Created .Net Core MVC Website. Implemented Entity Framework for SQL and created Administration Management page to allow moderators to add participant results. Designed the website to send emails to participants via a link with a generated ID for participants to allow them check their status.',
        link: 'https://docker331.herokuapp.com/Home/'
      },
      {
        avatar: '',
        frontpage: 'frontpage/fisherman.jpg',
        title: 'Fishermen',
        subtitle: 'C#, HTML, JavaScript, CSS, SQL',
        subtitle2: 'NuxtJS, API NetCore, Vuetify',
        text: 'Created Front End Vue framework. Then connect to .Net Core WebAPI to get data. Graph the best month to fish. Graph best place to fish. Write Custom Query to do filter and sort any column.',
        link: 'https://fishermen.azurewebsites.net/'
      },
      {
        avatar: '',
        frontpage: 'frontpage/informationgather.jpg',
        title: 'Information Gather',
        subtitle: 'C#',
        subtitle2: 'Xamarin Android',
        text: "Create an Android app that collect users' information. The app can generate multiple forms then writes to csv on internal storage. It supports function to send email and local authentication to make sure no one use your app without your permission.",
        link: 'https://photos.app.goo.gl/uSErTi7Ycc3ogJDc7'
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
    }
  }
}
</script>

<style scoped>

</style>
