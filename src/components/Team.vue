<template>
<div class="Team">
    <h1 class="subheading grey--text text-center mt-5 mb-6">Team</h1>

    <v-container>
        
        <v-row wrap>
        <v-col xs="12" sm="6" md="4" lg="3" v-for="person in team" :key="person.name">
          <v-card text class="text-center ma-3 grey lighten-4">
            <v-responsive class="pt-4">
                <v-avatar size="80">
                    <img :src="person.avatar">
                </v-avatar>
            </v-responsive>
            <v-card-text>
              <div class="subheading">{{ person.name }}</div>
              <div class="grey--text">{{ person.role }}</div>
            </v-card-text>
            <v-card-actions>
              <v-btn elevation="0">
                <v-icon small left>mdi-android-messages</v-icon>
                <span class="">Message</span>
              </v-btn>
              <!-- <v-btn elevation="0">
                <v-icon small left>mdi-android-messages</v-icon>
                <span class="">Assign Task</span>
              </v-btn> -->
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>


    </v-container>
 

</div>
</template>
 
<script>
export default {
    data() {
    return {
      team: [
        { name: 'Pratik N', role: 'Full-Stack developer', avatar: "/avatar-1.png" },
        { name: 'Gayatri N', role: 'Graphic designer', avatar: "/avatar-5.png" },
        { name: 'Prachi Ni', role: 'Web developer', avatar: "/avatar-3.png" },
        { name: 'Mohit K', role: 'Social media', avatar: "/avatar-4.png" }
      ]
    }
  }
}
</script>