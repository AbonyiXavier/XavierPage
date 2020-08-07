<template>
  <div class="home">
    <v-container>
      <!-- Toogle theme -->
      <div class="d-flex flex-row-reverse">
        <v-switch @click="toogleTheme" text v-model="Dark" class="ma-4" :label="theme"></v-switch>
      </div>
      <div class>
        <!-- Image & Resume -->
        <v-row align="center">
          <v-hover v-slot:default="{ hover }">
            <v-col cols="12" sm="4">
              <v-row justify="center">
                <v-avatar color size="240">
                  <v-img :src="require('../assets/photo.jpg')" aspect-ratio="1" contain>
                    <v-expand-transition>
                      <div
                        v-if="hover"
                        class="d-flex transition-fast-in-fast-out grey darken-1 v-card--reveal display-2 white--text"
                        style="height: 100%;"
                      >Abonyi Xavier</div>
                    </v-expand-transition>
                  </v-img>
                </v-avatar>
                <div>
                  <h4 class="blue--text"></h4>
                </div>
              </v-row>
            </v-col>
          </v-hover>
          <v-spacer></v-spacer>

          <v-col sm="4">
            <v-row justify="center">
              <a href="./Resume.pdf" target="_blank">
                <span class="resume">Resume</span>
              </a>
            </v-row>
          </v-col>
        </v-row>
        <!-- About me -->
        <div>
          <div align="center">
            <h2 class="mt-2">ABOUT ME</h2>
            <p>
              A skilled and ambitious full stack developer seeking to make a direct impact on a company’s business,
              operations and experience. Bringing practical experience and knowledge of JavaScript UI technologies,
              HTML5, CSS3, Vue.js, Node.js, MySQL, PostgreSQL, Mocha.js and
              creating RESTful APIs for a thriving, exciting, and growing company
            </p>
          </div>
          <v-sheet height="400" class="overflow-hidden" style="position: relative;">
            <v-container class="fill-height">
              <v-row align="center" justify="center">
                <v-btn color="dark" dark @click.stop="drawer = !drawer">CLICK MY PROJECTS</v-btn>
              </v-row>
            </v-container>

            <v-navigation-drawer v-model="drawer" absolute temporary width="500">
              <v-list-item>
                <v-list-item-avatar>
                  <v-img :src="require('../assets/photo.jpg')"></v-img>
                </v-list-item-avatar>

                <v-list-item-content>
                  <v-list-item-title>Abonyi Nnamdi Francis</v-list-item-title>
                </v-list-item-content>
              </v-list-item>

              <v-divider></v-divider>

              <v-list dense>
                <v-list-item v-for="item in items" :key="item.title" link>
                  <v-btn
                    text
                    dense
                    retain-focus-on-click
                    href="https://x-todo-list.netlify.app/"
                  >{{ item.title }}</v-btn>
                  <v-btn
                    text
                    dense
                    retain-focus-on-click
                    href="http://embarrassed-camera.surge.sh"
                  >{{ item.title2 }}</v-btn>
                  <v-list-item-content></v-list-item-content>
                </v-list-item>
              </v-list>
            </v-navigation-drawer>
          </v-sheet>
        </div>
      </div>
    </v-container>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: "Home",
  components: {},
  data() {
    return {
      drawer: null,
      items: [
        { title: "TodoList" },
        { title2: "The Venue" }
        // { title: "Home", link: "dashboard" },
        // { title: "About", link: "question_answer" }
      ]
    };
  },
  computed: {
    theme() {
      if (this.$vuetify.theme.dark) {
        return "Light";
      } else {
        return "Dark";
      }
    }
  },
  methods: {
    toogleTheme() {
      this.$vuetify.theme.dark = !this.$vuetify.theme.dark;
    }
  }
};
</script>
<style scoped>
a {
  text-decoration: none;
}
a .resume {
  font-size: 25px;
}

.v-card--reveal {
  align-items: center;
  bottom: 0;
  justify-content: center;
  opacity: 0.5;
  position: absolute;
  width: 100%;
}
</style>