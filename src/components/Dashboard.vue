<template>
<div class="dashboard">


  <h1 class="subheading grey--text text-center mt-5 mb-6">Dashboard</h1>



    <v-container class="grey lighten-4">

      <v-row justify-start class="mb-3 ml-3">
        <v-col>
          <v-btn @click="sortBy('title')" elevation="0">
            <v-icon small left>mdi-folder-text</v-icon>
            <span class=" text-lowercase" > By project name</span>
          </v-btn>
          <v-btn @click="sortBy('person')" elevation="0">
            <v-icon small left>mdi-face</v-icon>
            <span class=" text-lowercase" >By Person</span>
          </v-btn>
        </v-col>
        <v-col sm="6" md="4">
          <v-form ref="form" v-model="valid" lazy-validation >
            <v-text-field v-model="search" label="search" md="2"></v-text-field>
            <v-btn class="mr-3 primary" text >
              <!-- <v-icon small left>mdi-person_search</v-icon> -->
              <span>Search</span>
            </v-btn>
          </v-form>
        </v-col>
      </v-row>



      <v-card text class="pa-3" >
        <v-row :class="`pa-3 project ${project.status}`" no-gutters v-for="project in projects" :key="project.title">
          <v-col sm="12" md="6">
              <div class="caption">Project Title</div>
              <div>{{project.title}}</div>
          </v-col>
          <v-col sm="4" md="2">
              <div class="caption">Person</div>
              <div>{{project.person}}</div>
          </v-col>
          <v-col sm="4" md="2">
              <div class="caption">Due By</div>
              <div>{{project.due}}</div>
          </v-col>
          <v-col sm="4" md="2">
              <div class="float-right">
                <v-chip small :class="`${project.status} my-2 caption`">{{ project.status }}</v-chip>
              </div>
          </v-col>
        </v-row>
        <!-- <v-divider></v-divider> -->
      </v-card>
    </v-container>
    
 

</div>
</template>
 

<script>
export default {
    // name:'Home',
    props:{
        msg: String
    },

    data(){
      return{
          projects:[
            { title: 'Design a new website', person: 'Pratik N', due: '1st Jan 2019', status: 'ongoing', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'},
            { title: 'Code up the homepage', person: 'Mohit K', due: '10th Jan 2019', status: 'complete', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'},
            { title: 'Design video thumbnails', person: 'Prachi N', due: '20th Dec 2018', status: 'complete', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'},
            { title: 'Create a community forum', person: 'Gayatri N', due: '20th Oct 2018', status: 'overdue', content: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'},
      ],
      valid: false,
      search: '',      
      }
      
    },

  methods: {
    sortBy(prop) {
      this.projects.sort((a,b) => a[prop] < b[prop] ? -1 : 1)
    }
  }
}
</script>


<style>
.project.complete{
  border-left: 6px solid skyblue;
}
.project.ongoing{
  border-left: 6px solid orange
}
.project.overdue{
  border-left: 6px solid tomato;
}
.v-chip.complete{
  background: skyblue;
}
.v-chip.ongoing{
  background: orange;
}
.v-chip.overdue{
  background: tomato;
}
</style>