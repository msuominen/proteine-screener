<template>
  <b-container class="home">
    <b-row class="pt-2">
      <b-col cols="12" md="6">
        <img class="img-fluid" src="../assets/logo_promiss.png" />
      </b-col>
      <b-col cols="12" md="6">
        <p>{{ $t('content') }}</p>
      </b-col>

      <b-col cols="12" class="text-center">
        <router-link class="btn btn-secondary btn-lg" :to="{ name: 'screener', params: { question: 1 }}">{{ $t('home.button.title') }}</router-link>
      </b-col>
      <b-col cols="12" class="text-center">
        <b-form-checkbox id="checkbox1"
          :checked="autoNext"
          @change="changeAutoNext"
          value="1"
          unchecked-value="0">
          Auto Next
        </b-form-checkbox>
      </b-col>
    </b-row>
    <b-row>
    </b-row>
  </b-container>
</template>

<script>
import { mapGetters } from 'vuex'

export default {
  name: 'Home',
  computed: {
    ...mapGetters({
      autoNext: 'quiz/autoNext',
      locales: 'config/locales'
    })
  },
  methods: {
    changeAutoNext (val) {
      this.$store.commit('quiz/setAutoNext', val)
    }
  }
}
</script>

