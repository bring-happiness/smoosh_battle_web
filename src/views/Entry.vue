<template>
  <div class="entry">
    <v-container>

      <v-row>

        <v-col cols="12"
               class="header"
        >
          <img src="@/assets/logo-rounded.png" alt="Logo Smoosh Battle">

          <h1>Smoosh Battle</h1>
        </v-col>

      </v-row>

      <v-row justify="center">
        <v-col cols="4">

          <div class="email-info text--white">
            Enter email to access the game
          </div>

          <v-text-field
            v-model="email"
            label="Your email"
            placeholder="youremail@gmail.com"
            :rules="emailRules"
            filled
            class="email-input"
          ></v-text-field>
        </v-col>
      </v-row>

      <v-row justify="center">
        <v-col cols="4">

          <v-row justify="center">
            <v-btn
              @click="play"
              class="btn-play"
              :class="{ 'disabled': !isEmailValid }"
              x-large
              elevation="24"
              rounded
            >
              <v-icon>mdi-microsoft-xbox-controller</v-icon>
              <span class="text">Play !</span>
            </v-btn>
          </v-row>

        </v-col>

      </v-row>

      <v-row class="additionnal-infos" justify="center">
        <v-col cols="5">

          <h3>We will notify you when :</h3>
          <p><span class="dot"></span>New characters, features and modes coming in the demo</p>

          <br>

          <p><span class="dot"></span>Beta released with weekly tournaments
            where you can earn real life gifts</p>
        </v-col>
      </v-row>

    </v-container>
  </div>
</template>

<script>
export default {
  name: 'Entry',

  data() {
    return {
      email: '',
      emailRules: [
        (v) => !!v || 'E-mail is required',
        (v) => /.+@.+\..+/.test(v) || 'E-mail must be valid',
      ],
    };
  },

  computed: {
    isEmailValid() {
      for (let i = 0; i < this.emailRules.length; i += 1) {
        const methodResult = this.emailRules[i](this.email);

        if (methodResult !== true) {
          return false;
        }
      }

      return true;
    },
  },

  methods: {
    play() {
      if (!this.isEmailValid) {
        return;
      }

      console.log('alors?');
      // go to demo !
    },
  },
};
</script>

<style lang="scss">
.entry {
  width: 100%;
  height: 100%;
  background: url("~@/assets/cover.png");
  background-size: cover;
}

.header {
  display: inline-flex;
  align-items: center;
  margin-top: 17px;

  h1 {
    color: #FDFDFD;
    margin-left: 17px;
    font-size: 2.3rem;
  }
}

.email-info {
  width: 100%;
  padding: 7px;
  background: rgba(0, 0, 0, 0.6);
  border-radius: 7px 7px 0 0;
  color: #FDFDFD;
  text-align: center;
}

.email-input {
  border-radius: 0 !important;
  background: transparent !important;

  .v-input__slot {
    margin: 0;
    background: #FDFDFD !important;
  }

  .v-text-field__details {
    padding: 11px !important;
    background: #333;
    margin: 0 !important;
    border-radius: 0 0 7px 7px;

    .v-messages {
      text-align: center;
      font-size: 0.9rem;
    }
  }
}

.btn-play {
  background: #FF3FBE !important;
  color: #FDFDFD !important;
  margin-bottom: 37px;

  &.disabled {
    opacity: 0.5;
  }

  .text {
    margin-left: 7px;
  }
}

.additionnal-infos {
  color: #FDFDFD;

  h3 {
    text-align: center;
    text-decoration: underline;
    font-size: 1em;
    margin-bottom: 7px;
    font-weight: normal;
  }

  p {
    position: relative;
    display: inline-block;
    font-size: 0.9rem;
    margin-bottom: 7px !important;
  }

  .dot {
    position: absolute;
    left: -12px;
    top: 6px;
    content: "";
    height: 7px;
    width: 7px;
    background-color: #FDFDFD;
    border-radius: 50%;
    display: inline-block;
  }
}
</style>
