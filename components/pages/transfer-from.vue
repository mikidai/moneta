<template>
  <div>
    <v-subheader class="header">振込元</v-subheader>
    <v-list-item two-lines>
      <v-list-item-content>
        <v-list-item-title>
          <v-layout>
            <v-flex xs4>{{ bank | name }}</v-flex>
            <v-flex xs1>{{ account.kind }}</v-flex>
            <v-flex xs3>{{ account.num }}</v-flex>
            <v-flex xs1>残高</v-flex>
            <v-flex xs3>{{ account.total | yen }}</v-flex>
          </v-layout>
        </v-list-item-title>
        <v-list-item-title>
          <v-layout>
            <v-flex xs4>{{ branch | name }}</v-flex>
            <v-flex xs4>{{ account | name }}</v-flex>
            <v-flex xs1>振込後</v-flex>
            <v-flex xs3>{{ (account.total - amount - fee) | yen }}</v-flex>
          </v-layout>
        </v-list-item-title>
      </v-list-item-content>
    </v-list-item>
    <v-divider />
  </div>
</template>

<script>
import { mapGetters } from "vuex";

export default {
  middleware: "login",
  computed: {
    ...mapGetters("login", ["account", "branch", "bank"]),
    ...mapGetters("transfer", ["amount", "fee"]),
  },
};
</script>
