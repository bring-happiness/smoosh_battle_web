<template>
  <div class="main-container">

    <v-navigation-drawer
      width="300"
      style="position: absolute"
      v-model="drawerOpen"
      :mini-variant.sync="drawerMini"
      permanent
      right
    >

      <div class="d-flex flex-column" style="height: 99%;">
        <v-list-item class="px-2" style="flex: 0 40px;">
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

        <transition :name="pageTransition" mode="out-in">

          <div
            v-if="page === 'HOME'"
            key="home"
            class="page-home"
          >

            <v-list dense>
              <v-list-item>
                <v-list-item-content>
                  <a
                    ref="app-store-link"
                    href="https://apps.apple.com/us/app/smoosh-battle/id1611349442"
                    target="_blank"
                  >
                    <img
                      src="@/assets/stores/app_store.png"
                      alt="Download on App Store"
                    >
                  </a>
                </v-list-item-content>

                <v-list-item-content>
                  <a
                    ref="apk-download"
                    href="@/assets/smoosh_battle.apk"
                    target="_blank"
                    download
                  >
                    <img
                      src="@/assets/stores/google_play.png"
                      alt="Download on Google Play">
                  </a>

                  <!--<v-btn
                    class="btn-get-app"
                    @click="goToDownloadPage"
                  >
                    Get the app
                  </v-btn>-->
                </v-list-item-content>
              </v-list-item>

              <!--<v-list-item
                link
              >
                <v-list-item-content>
                  <v-btn
                    class="btn-find-players"
                    @click="goToFindPlayer"
                  >
                    Find players
                  </v-btn>
                </v-list-item-content>
              </v-list-item>-->

              <v-list-item
                link
              >
                <v-list-item-content>
                  <v-btn
                    class="btn-give-feedback"
                    @click="goToFeedback"
                  >
                    Give feedback
                  </v-btn>
                </v-list-item-content>
              </v-list-item>

            </v-list>

            <v-divider></v-divider>

            <div class="content">

              <div
                @click="page = 'TUTOS'"
                class="d-flex section"
              >
                <div>
                  <v-icon>mdi-play-circle</v-icon>
                </div>

                <div class="text">Tutorials videos</div>
              </div>

              <div
                @click="page = 'CHARACTERS'"
                class="d-flex section">
                <div>
                  <v-icon>mdi-account-group</v-icon>
                </div>

                <div class="text">New characters coming</div>
              </div>

            </div>

            <v-divider></v-divider>
          </div>

          <div
            v-if="page === 'TUTOS'"
            key="tutos"
            class="page-tutos"
          >

            <v-icon
              @click="page = 'HOME'"
              class="close">mdi-arrow-left-circle</v-icon>

            <h1>Tutorials</h1>

            <!--<div class="tuto how-to-win">
              <youtube
                class="video"
                video-id="YdrR9SqVDwc"
                ref="youtube"
              ></youtube>

              <div>How to win ?</div>
            </div>-->

            <div class="tuto teleport">
              <youtube
                class="video"
                video-id="6OEl-r54epQ"
                ref="youtube"
              ></youtube>

              <div>How to  teleport ?</div>
            </div>

            <div class="tuto fire-direction">
              <youtube
                class="video"
                video-id="YdrR9SqVDwc"
                ref="youtube"
              ></youtube>

              <div>How to control fire direction ?</div>
            </div>

          </div>

          <div
            v-if="page === 'CHARACTERS'"
            key="characters"
            class="page-characters"
          >

            <v-icon
              @click="page = 'HOME'"
              class="close">mdi-arrow-left-circle</v-icon>

            <h1>Coming soon</h1>

            <div class="character tanker">
              <img
                src="@/assets/characters/tanker.png"
                alt="Tanker"
              />

              <div>Tanker</div>
            </div>

            <v-divider></v-divider>

            <div class="character mole">
              <img
                src="@/assets/characters/mole.png"
                alt="Mole"
              />

              <div>Mole</div>
            </div>

            <v-divider></v-divider>

            <div class="character robber">
              <img
                src="@/assets/characters/robber.png"
                alt="Robber"
              />

              <div>Robber</div>
            </div>

          </div>

        </transition>

        <v-spacer></v-spacer>

        <div class="social-media d-block mb-2">

          <div class="text-center mb-1">
            <a href="https://discord.com/channels/941359292592844922/941359292592844925" target="_blank">
              <img
                src="@/assets/social-media/discord.png"
                width="60"
                height="60"
                alt="Discord"
              >
            </a>
          </div>

          <div class="d-flex justify-space-around">
            <a href="https://twitter.com/SmooshBattle" target="_blank">
              <img src="@/assets/social-media/twitter.png" alt="Twitter">
            </a>

            <a href="https://www.facebook.com/smooshbattle" target="_blank">
              <img src="@/assets/social-media/facebook.png" alt="Facebook">
            </a>

            <a href="https://www.instagram.com/smoosh_battle/" target="_blank">
              <img src="@/assets/social-media/instagram.png" alt="Instagram">
            </a>

            <a href="https://www.youtube.com/channel/UCxHjzCPhxAn7DQECHuxakvQ" target="_blank">
              <img src="@/assets/social-media/youtube.png" alt="Youtube">
            </a>

            <a href="https://www.reddit.com/r/SmooshBattle/" target="_blank">
              <img src="@/assets/social-media/reddit.png" alt="Reddit">
            </a>
          </div>

        </div>
      </div>
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

  mounted() {
    // If iOS or Android
    if (this.getMobileOS() === 'android') {
      this.$refs['apk-download'].click();
    } else if (this.getMobileOS() === 'ios') {
      this.$refs['app-store-link'].click();
    }
  },

  data() {
    return {
      drawerOpen: true,
      drawerMini: false,
      page: 'HOME', // can be 'HOME', 'TUTOS' or 'CHARACTERS'
    };
  },
  computed: {
    pageTransition() {
      return this.page !== 'HOME' ? 'slide-fade' : 'slide-fade-reversed';
    },
  },
  methods: {
    getMobileOS() {
      const ua = navigator.userAgent;

      if (/android/i.test(ua)) {
        return 'android';
      }
      if (/iPad|iPhone|iPod/.test(ua)
        || (navigator.platform === 'MacIntel' && navigator.maxTouchPoints > 1)) {
        return 'ios';
      }
      return 'other';
    },
    /* goToDownloadPage() {
      window.open('https://smooshbattle.itch.io/smoosh-battle', '_blank');
    }, */
    goToFindPlayer() {
      window.open('https://discord.com/channels/941359292592844922/941359746626257007', '_blank');
    },
    goToFeedback() {
      window.open('https://discord.com/channels/941359292592844922/941359768767955024', '_blank');
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

.btn-find-players {
  background: #6200EE !important;
  color: #FDFDFD !important;
}

.btn-give-feedback {
  background: #6200EE !important;
  color: #FDFDFD !important;
}

.content {

  .section {
    padding: 11px 17px;
    align-items: baseline;

    &:hover {
      cursor: pointer;
      background: rgba(98, 0, 238, 0.3);

      .text {
        color: #FDFDFD;
      }
    }

    .v-icon {
      color: #6200EE !important;
      margin-right: 17px;
    }

    .text {
      color: rgba(0, 0, 0, 0.6);
      font-weight: 500;
      font-size: 14px;
    }
  }
}

.page-tutos, .page-characters {
  position: relative;

  .close {
    position: absolute;
    left: 7px;
    top: 6px;
    color: #6200EE;
  }

  h1 {
    color: #121212;
    font-size: 14px !important;
    font-weight: 500;
    letter-spacing: 1px;
    text-transform: uppercase;
    text-align: center;
    margin: 7px 0;
  }
}

.page-tutos {
  text-align: center;

  h1 {
    margin-bottom: 17px;
  }

  .tuto {

    .video {
      width: 100%;
      height: 120px;
    }

    div {
      margin-top: -4px;
      margin-bottom: 13px;
      font-weight: 500;
      color: rgba(0, 0, 0, 0.6);
      font-size: 0.9rem;
    }
  }
}

.page-characters {

  hr {
    width: 80%;
    margin-left: 10%;
  }

  .character {
    text-align: center;
    margin-top: 27px;
    margin-bottom: 7px;

    &.tanker {
      margin-top: 47px;
    }

    img {
      width: 100px;
    }

    div {
      font-weight: 500;
      color: rgba(0, 0, 0, 0.6);
      font-size: 0.9rem;
      margin-top: 3px;
    }
  }
}

.social-media {

  img {
    &:hover {
      opacity: 0.6;
    }
  }
}
</style>
