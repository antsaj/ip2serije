<template>
  <v-app id="inspire">
    <v-app-bar app dark>
      <v-app-bar-nav-icon @click="drawer = true"></v-app-bar-nav-icon>

      <v-toolbar-title>Serije</v-toolbar-title>

      <v-spacer></v-spacer>

      <v-navigation-drawer app v-model="drawer" absolute temporary dark>
        <v-list nav dense>
          <v-list-item-group
            v-model="group"
            active-class="deep-purple--text text--accent-4"
          >
            <v-row>
              <v-col cols="1">
                <br>  
                <v-btn v-for="link in links" :key="link.text" text :to="link.path">
                  {{ link.text }}
                </v-btn>
              </v-col>
            </v-row>
          </v-list-item-group>
        </v-list>
      </v-navigation-drawer>
    </v-app-bar>
    <v-main>
      <router-view />
    </v-main>

    <v-footer class="text-center" style="height:100px; background-color:#2f2f2f">
      <v-container>
        <v-btn
          v-for="icon in icons"
          :key="icon.icon"
          class="mx-6 white--text"
          icon
        >
        <a :href="icon.path" target="_blank" class="hrefEle">
          <v-icon size="44px" class="icon" >
            {{ icon.icon }}
          </v-icon>
        </a>
        </v-btn>
      </v-container>
    </v-footer>


  </v-app>
</template>

<script>
export default {
  name: "App",

  data: () => ({
    drawer: false,
    group: null,
    links: [
      {
        text: "Početna",
        path: "/",
      },
      {
        text: "Pretraživanje serija",
        path: "/ShowSearch",
      },
      {
        text: "Sve serije",
        path: "/AllShows",
      },
      {
        text: "Prijava",
        path: "/login",
      },
    ],
    icons: [
      {
          icon: "mdi-facebook",
          path: "https://www.facebook.com/fpmoz.ba/?locale=hr_HR"
      },
      {
          icon: "mdi-youtube",
          path: "https://www.youtube.com/@studijinformatike-fpmoz2231"
      },
      {
          icon: "mdi-google",
          path: "https://www.google.com"
      },
      {
          icon: "mdi-instagram",
          path: "https://www.instagram.com/fpmoz.mostar/?hl=hr"
      },
    ],
  }),
};
</script>

<style lang="scss" scoped>
main {
  background-image: url("assets/miles.jpeg"); 
  background-size: 100% 100%;
  background-attachment: fixed;
}


.hrefEle{
  text-decoration: none;
  color: white;
}
.icon:hover{
  scale:200%
  
}
</style>