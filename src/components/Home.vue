<template>
 <v-container>
   <v-layout row wrap class="mb-2">
     <v-flex xs12 sm6 class="text-xs-center text-sm-right">
       <v-btn large router to="/meetups" class="info">Explore Meetups</v-btn>
     </v-flex>
     <v-flex xs12 sm6 class="text-xs-center text-sm-left">
       <v-btn large router to="/meetup/new" class="info">Organize Meetups</v-btn>
     </v-flex>
   </v-layout>
   <v-layout row wrap class="mt-2">
     <v-flex xs12>
       <v-carousel>
         <v-carousel-item
         v-for="(item, i) in meetups"
         v-bind:src="item.imageUrl"
         :key="i"
         @click="onLoadMeetup(item.id)"
         >
           <div class="title text-xs-center">
           {{item.title}}
         </div>
         </v-carousel-item>
       </v-carousel>
     </v-flex>
   </v-layout>
   <v-layout row wrap class="mt-2">
     <v-flex xs12  class="text-xs-center">
      <p>Join our awesome meetups!</p>
     </v-flex>
   </v-layout>
 </v-container>
</template>

<script>
export default {
  data () {
    return {

    }
  },
  methods: {
    onLoadMeetup (id) {
      this.$router.push('/meetup/' + id)
    }
  },
  computed: {
    meetups () {
      return this.$store.getters.featuredMeetups
    }
  }
}
</script>
<style scoped>
  .title {
    position: absolute;
    bottom: 50px;
    text-align: center;
    background-color: rgba(0, 0, 0, 0.5);
    color: white;
    font-size: 2em;
    padding: 20px;
  }
</style>
