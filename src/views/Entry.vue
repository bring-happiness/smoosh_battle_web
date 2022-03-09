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
        <v-col cols="10" :sm="6" :md="4" :xl="3">

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

          <vue-mailchimp-email-signup-form
            class="mailchimp-email-signup-form"
            :element-id="'landing-email-signup-form'"
            :url="mailchimpUrl"
            :title="''"
          />
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
        <v-col cols="10" :sm="6" :md="4" :xl="3">

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
import { VueMailchimpEmailSignupForm } from 'vue-mailchimp-email-signup-form';

export default {

  name: 'Entry',

  created() {
    const emailStored = localStorage.getItem('email');

    if (emailStored != null) {
      this.$router.push({ name: 'Game' });
    }
  },

  components: {
    'vue-mailchimp-email-signup-form': VueMailchimpEmailSignupForm,
  },

  data() {
    return {
      email: '',
      emailRules: [
        (v) => !!v || 'E-mail is required',
        (v) => /.+@.+\..+/.test(v) || 'E-mail must be valid',
      ],
      mailchimpUrl: 'https://gmail.us20.list-manage.com/subscribe/post?u=308a9119721f157ef973b8af9&id=8264aeb3c8',
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

  watch: {
    email(newValue) {
      document.querySelector('#landing-email-signup-formmce-EMAIL').value = newValue;
    },
  },

  methods: {
    play() {
      if (!this.isEmailValid) {
        return;
      }

      localStorage.setItem('email', this.email);

      document.querySelector('#landing-email-signup-formmc-embedded-subscribe').click();
      // this.$router.push({ name: 'Game' });
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

.mailchimp-email-signup-form {
  display: none;
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
