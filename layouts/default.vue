<template>
  <v-app>
    <v-app-bar app>
      <v-app-bar-nav-icon>
        <nuxt-link to="/" tag="div">
          <v-icon>mdi-bank</v-icon>
        </nuxt-link>
      </v-app-bar-nav-icon>
      <v-toolbar-title>
        <p class="body-1 my-0">{{ bank | name }}</p>
        <p class="body-1 my-0">{{ branch | name }}</p>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-toolbar-items>
        <v-btn class="title" @click=" text">{{ account | name }}様</v-btn>
      </v-toolbar-items>
    </v-app-bar>
    <v-content>
      <v-container fluid>
        <v-layout align-start justify-center>
          <v-flex xs12 sm12 md8 xl8>
            <nuxt />
          </v-flex>
        </v-layout>
      </v-container>
      <code v-if="debug">{{ $store.state }}</code>
    </v-content>
  </v-app>
</template>

<script>
import { mapGetters } from "vuex";

export default {
  data: () => ({
    debug: false,
  }),
  computed: {
    ...mapGetters("login", ["account", "branch", "bank"]),
  },
  methods: {
    text() {
      if (window.confirm("ログアウトしますか？")) {
        this.$router.push("/login");
      } else {
        window.alea;
      }
    },
  },
};
</script>
