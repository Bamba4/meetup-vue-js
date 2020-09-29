<template>
 <v-container>
   <v-layout row wrap>
     <v-flex xs12>
       <v-card
         class="mx-auto"
         max-width="1000"
       >
         <v-card-title class="primary--text">
           {{ meetup.title }}
         </v-card-title>
         <v-img
           :src="meetup.imageUrl"
           height="400px"
         ></v-img>
         <v-card-text>
           <div class="info--text">{{ meetup.date | data }} - {{ meetup.location }}</div>
           <div>{{ meetup.description }}</div>
         </v-card-text>
         <v-card-actions>
           <v-spacer></v-spacer>

           <v-btn class="primary">REGISTER</v-btn>
         </v-card-actions>

         <v-expand-transition>
           <div v-show="show">
             <v-divider></v-divider>

             <v-card-text>
               I'm a thing. But, like most politicians, he promised more than he could deliver. You won't have time for sleeping, soldier, not with all the bed making you'll be doing. Then we'll go with that data file! Hey, you add a one and two zeros to that or we walk! You're going to do his laundry? I've got to find a way to escape.
             </v-card-text>
           </div>
         </v-expand-transition>
       </v-card>
     </v-flex>
   </v-layout>
 </v-container>
</template>

<script>
export default {
  name: 'Meetup',
  props: ['id'],
  computed: {
    meetup () {
      return this.$store.getters.loadedMeetup(this.id)
    }
  }
}
</script>

<style scoped>

</style>
