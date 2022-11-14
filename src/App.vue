<template>
  <v-app>
    <v-navigation-drawer v-model="drawer" app clipped flating temporary>
      <v-list dense>
        <v-row class="ma-2 mb-3">
          <v-icon class="mx-4" large>mdi-video</v-icon>
          <v-tollbar-title class="align-center">
            <span class="title">VueTube</span>
          </v-tollbar-title>
        </v-row>
        <v-list-item v-for="item in items" :key="item.icon" link>
          <v-list-action class="mx-1">
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-action>
          <v-list-item-content>
            <v-list-item-title>{{ item.text }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar app clipped-left>
      <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
      <v-icon class="mx-4" large>mdi-video</v-icon>
      <v-tollbar-title class="align-center">
        <span class="title">VueTube</span>
      </v-tollbar-title>
      <v-spacer></v-spacer>
      <v-text-field
        class="mt-6"
        placeholder="Ara.."
        single-line
        append-icon="mdi-magnify"
        color="white"
        solo
      ></v-text-field>
      <v-spacer></v-spacer>
      <v-btn class="ml-0" icon>
        <v-icon>mdi-apps</v-icon>
      </v-btn>
      <v-btn class="ma-2" icon>
        <v-icon>mdi-bell</v-icon>
      </v-btn>
      <div>
        <v-menu
          v-model="menu"
          offset-y
          :close-on-content-click="false"
          :nudge-witdh="250"
        >
          <template v-slot:activator="{ on }">
            <v-avatar size="45" color="red">
              <span v-on="on" class="white--text text-h5">KA</span>
            </v-avatar>
          </template>
          <v-card>
            <v-list>
              <v-list-item>
                <v-list-item-avatar>
                  <v-avatar size="45" color="red">
                    <span v-on="on" class="white--text">KA</span>
                  </v-avatar>
                </v-list-item-avatar>
                <v-list-content>
                  <v-list-item-title>Kadriye Akoğlu</v-list-item-title>
                  <v-list-item-subtitle> VueCode</v-list-item-subtitle>
                </v-list-content>
              </v-list-item>
            </v-list>
            <v-divider></v-divider>
            <v-list>
              <v-list-item>
                <v-list-item-action>
                  <v-icon>mdi-cog</v-icon>
                </v-list-item-action>
                <v-list-item-title>Ayarlar</v-list-item-title>
              </v-list-item>
            </v-list>
            <v-list>
              <v-list-item>
                <v-list-item-action>
                  <v-switch v-model="theme" color="purple"></v-switch>
                </v-list-item-action>
                <v-list-item-title>Karanlık Tema</v-list-item-title>
              </v-list-item>
            </v-list>
            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn color="primary" text @click="menu = false"
                >ÇIKIŞ YAP</v-btn
              >
            </v-card-actions>
          </v-card>
        </v-menu>
      </div>
    </v-app-bar>
    <div>
      <v-content>
        <v-container>
          <v-row class="mb-4">
            <v-col
              sm="6"
              md="4"
              lg="3"
              xl="2"
              v-for="(item, index) in 200"
              :key="index"
            >
              <v-card>
                <v-img
                  height="200px"
                  :src="`http://picsum.photos/500/300?images=${index + 1}`"
                  :lazy-src="`http://picsum.photos/10/7?images=${index + 1}`"
                >
                </v-img>
                <v-card-subtitle class="">Number {{ item }}</v-card-subtitle>
                <v-card-text class="text--primary">
                  <div>Başlık Alanı</div>
                  <div>Başlık içeriği</div>
                </v-card-text>
                <v-cart-action>
                  <v-btn color="orange" text>Kaydet</v-btn>
                  <v-btn color="orange" text>Paylaş</v-btn>
                </v-cart-action>
              </v-card>
            </v-col>
          </v-row>
        </v-container>
      </v-content>
    </div>
  </v-app>
</template>

<script>
export default {
  name: "App",

  data: () => ({
    items: [
      { icon: "mdi-home-outline", text: "Anasayfa" },
      { icon: "mdi-trending-up", text: "Popüler İçerik" },
      { icon: "mdi-play-circle", text: "Videolarınız" },
      { icon: "mdi-history", text: "Geçmiş" },
      { icon: "mdi-thumb-up-outline", text: "Beğendiğim videolar" },
    ],
    drawer: false,
    menu: false,
    theme: false,
  }),
  watch: {
    theme: function (next) {
      this.$vuetify.theme.dark = next;
    },
  },
};
</script>
