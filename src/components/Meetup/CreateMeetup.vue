<template>
  <v-container>
    <v-layout row>
      <v-flex xs12 sm6 offset-sm4>
        <h2 class="secondary--text">Create a new meetup</h2>
      </v-flex>
    </v-layout>
    <v-layout row>
      <v-flex xs12>
        <form @submit.prevent="onCreateMeetup">
          <v-layout row>
             <v-flex xs12  sm6 offset-sm3>
               <v-text-field name="title" v-model="title" id="title" label="Title" required></v-text-field>
             </v-flex>
          </v-layout>
          <v-layout row>
             <v-flex xs12  sm6 offset-sm3>
               <v-text-field name="location" v-model="location" id="location" label="Location" required></v-text-field>
             </v-flex>
          </v-layout>
          <v-layout row>
             <v-flex xs12  sm6 offset-sm3>
               <v-text-field name="imageUrl" v-model="imageUrl" id="image-url" label="Image Url" required></v-text-field>
             </v-flex>
          </v-layout>
          <v-layout row>
            <v-flex xs12 sm6 offset-sm3>
              <img :src="imageUrl" height="200px">
            </v-flex>
          </v-layout>
          <v-layout row>
             <v-flex xs12  sm6 offset-sm3>
               <v-textarea
                 name="input-7-1"
                 label="Description"
                 v-model="description"
               ></v-textarea>
             </v-flex>
          </v-layout>
          <v-layout>
            <v-flex xs12 sm6 offset-sm3>
              <v-btn
                class="primary"
                :disabled="!formIsValid"
                type="submit"
              >Create meetup</v-btn>
            </v-flex>
          </v-layout>
        </form>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
export default {
  name: 'CreateMeetup',
  data () {
    return {
      title: '',
      imageUrl: '',
      description: '',
      location: ''
    }
  },
  computed: {
    formIsValid () {
      return this.title !== '' &&
        this.location !== '' &&
        this.description !== '' &&
        this.imageUrl !== ''
    }
  },
  methods: {
    onCreateMeetup () {
      if (!this.formIsValid) {
        return
      }
      const meetup = {
        title: this.title,
        imageUrl: this.imageUrl,
        description: this.description,
        location: this.location,
        date: new Date()
      }
      this.$store.dispatch('createMeetup', meetup)
      this.$router.push('/meetups')
    }
  }
}
</script>

<style scoped>

</style>
