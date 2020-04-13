<template>
  <div>
    <v-row v-for="i in Math.ceil(projects.length/projectPerRow)" :key="i*1.083">
      <v-col v-for="j in projectPerRow" :key="j*3.083">
        <v-card
          v-if="indexComputed(i,j) < projects.length"
          max-width="500"
          class="mx-auto"
        >
          <v-list-item>
            <v-list-item-content>
              <v-list-item-title class="headline">
                {{ projects[indexComputed(i,j)].title }}
              </v-list-item-title>
              <v-list-item-subtitle>{{ projects[indexComputed(i,j)].subtitle }}</v-list-item-subtitle>
              <v-list-item-subtitle>{{ projects[indexComputed(i,j)].subtitle2 }}</v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>
          <v-card-text>
            {{ projects[indexComputed(i,j)].text }}
          </v-card-text>

          <v-card-actions>
            <v-btn
              v-if="projects[indexComputed(i,j)].link"
              text
              color="deep-purple accent-4"
              :href="projects[indexComputed(i,j)].link"
              target="_blank"
            >
              Link
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </div>
</template>

<script>
export default {
  name: 'Project',
  data: () => ({
    projectPerRow: 3,
    projects: [
      {
        title: 'Mudbay',
        subtitle: 'PHP, Vue',
        subtitle2: 'WordPress',
        text: 'Create PHP API to cache data from SmartSheet to MySQL. Create four pages: ‘stores’, ‘store’, ‘events’, ‘brands’ by using Vue. Then implement these pages to existing WordPress. Built data driven templates that read data from smartsheets. Also mention that you built an integration with smartsheets that used custom built caching.',
        link: 'http://mudbay.com/'
      },
      {
        title: 'ACTiV',
        subtitle: 'C#, HTML, JavaScript, CSS',
        subtitle2: 'MVC Net Core, BootStrap 4',
        text: 'Migrate webforms template to MVC pattern. Implement Entity Framework for SQL. Implement Azure Ad Directory for Authentication. Implement DataTables.net for administration (View, Delete, Print, Add Comment). Implement OneClick to send email to users by using Azure Logic App.',
        link: 'http://www.goactiv.org/'
      },
      {
        title: 'ConnectMyVariant',
        subtitle: 'PHP, HTML, JavaScript, CSS, MySQL',
        subtitle2: 'Laravel, NuxtJs, Vuetify',
        text: 'Designed relational database. Used Laravel’s migration tool to create tables. Implemented API in Laravel to allow database functionality (read, create, delete). Implemented Nuxt SPA to create datatable and migrated it to existing Laravel project. Created HTML datatable to improve Search Engine Optimization (SEO). Created a NodeJS script to generate sitemap. Submitted final project to Google Search Console to improve SEO.',
        link: 'http://connectmyvariant.org/'
      },
      {
        title: 'Population Screening Study',
        subtitle: 'C#, HTML, JavaScript, CSS',
        subtitle2: 'MVC Net Core, BootStrap 4',
        text: 'Created .Net Core MVC Website. Implemented Entity Framework for SQL and created Administration Management page to allow moderators to add participant results. Designed the website to send emails to participants via a link with a generated ID for participants to allow them check their status.',
        link: 'https://docker331.herokuapp.com/Home/'
      },
      {
        title: 'Fishermen',
        subtitle: 'C#, HTML, JavaScript, CSS, SQL',
        subtitle2: 'NuxtJS, API NetCore, Vuetify',
        text: 'Created Front End Vue framework. Then connect to .Net Core WebAPI to get data. Graph the best month to fish. Graph best place to fish. Write Custom Query to do filter and sort any column.',
        link: 'https://fishermen.azurewebsites.net/'
      },
      {
        title: 'Information Gather',
        subtitle: 'C#',
        subtitle2: 'Xamarin Android',
        text: "Create an Android app that collect users' information. The app can generate multiple forms then writes to csv on internal storage. It supports function to send email and local authentication to make sure no one use your app without your permission.",
        link: 'https://photos.app.goo.gl/uSErTi7Ycc3ogJDc7'
      }
    ]
  }),
  created () {
    switch (this.$vuetify.breakpoint.name) {
      case 'xs':
        this.projectPerRow = 1
        break
      case 'sm':
        this.projectPerRow = 2
        break
      default:
        this.projectPerRow = 3
    }
  },

  methods: {
    indexComputed (i, j) {
      return (j - 1) + (i - 1) * this.projectPerRow
    }
  }
}
</script>

<style scoped>

</style>
