<template>
  <div class="main-container">

      <v-navigation-drawer
        style="position: absolute;"
        v-model="drawerOpen"
        :mini-variant.sync="drawerMini"
        permanent
        right
      >
        <v-list-item class="px-2">
          <v-list-item-avatar>
            <img src="@/assets/logo-rounded.png" alt="Logo Smoosh Battle">
          </v-list-item-avatar>

          <v-spacer></v-spacer>

          <v-btn
            icon
            @click.stop="drawerMini = !drawerMini"
          >
            <v-icon>mdi-chevron-right</v-icon>
          </v-btn>
        </v-list-item>

        <v-divider></v-divider>

        <v-list dense>
          <v-list-item
            link
          >
            <v-list-item-content>
              <v-btn
                class="btn-get-app"
                @click="goToDownloadPage"
              >
                Get the app
              </v-btn>
            </v-list-item-content>
          </v-list-item>
        </v-list>
      </v-navigation-drawer>

    <iframe
      frameborder="0"
      src="https://itch.io/embed-upload/5101122?color=333333"
      allowfullscreen
      style="width: 100vw; height: 100vh;"
    >
      <a href="https://smooshbattle.itch.io/smoosh-battle">Play Smoosh Battle on itch.io</a>
    </iframe>
  </div>
</template>

<script>
export default {

  created() {
    const emailStored = localStorage.getItem('email');

    if (emailStored === null) {
      this.$router.push({ name: 'Home' });
    }
  },

  data() {
    return {
      drawerOpen: true,
      drawerMini: false,
    };
  },
  methods: {
    goToDownloadPage() {
      window.location.href = 'https://smooshbattle.itch.io/smoosh-battle';
    },
  },
};
</script>

<style lang="scss">
.main-container {
  position: relative;
}

.btn-get-app {
  background: #FF3FBE !important;
  color: #FDFDFD !important;
}
</style>
