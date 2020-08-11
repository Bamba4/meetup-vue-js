<template>
  <v-container>
    <v-layout row wrap >
      <v-flex xs12 sm10 md8 offset-md1>
        <v-card class="info"  >
          <v-container fluid>
            <v-layout row v-for = "meetup in meetups" :key="meetup" class="mb-2">
              <v-flex xs5 sm4 md3>
                <v-card
                  class="mx-auto"
                  max-width="400"
                >
                  <v-img
                    class="white--text align-end"
                    height="150px"
                    :src="meetup.imageUrl"
                  >
                  </v-img>
                </v-card>
              </v-flex>
              <v-flex xs7 sm8 md9>
                <v-card-title primary-title>
                  <div>
                    <h1 class="white--text">{{ meetup.title }} </h1>
                    <p>{{ meetup.date }}</p>
                  </div>
                </v-card-title>
                <v-card-actions>
                  <v-icon left light>mdi-arrow</v-icon>
                  <v-btn text router :to="'/meetup/' + meetup.id">View Meetups</v-btn>
                </v-card-actions>
              </v-flex>
            </v-layout>
          </v-container>
        </v-card>
      </v-flex>
    </v-layout>
  </v-container>
</template>
<script>
export default {
  name: 'Meetups',
  computed: {
    meetups () {
      return this.$store.getters.loadedMetups
    }
  }
}
</script>
<style scoped>

</style>
