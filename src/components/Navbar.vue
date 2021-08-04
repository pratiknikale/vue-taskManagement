<template>
<nav>
    <v-toolbar text app color="teal lighten-2" dark>
        <v-app-bar-nav-icon @click.stop="drawer = !drawer" class="teal" elevation="8"></v-app-bar-nav-icon>
        <v-toolbar-title class="text-uppercase" >
            <span class="font-weight-light">Todo</span>
            <span class="text-lowercase">task</span>
        </v-toolbar-title>
        <v-spacer></v-spacer>
        <v-tab v-for="link in links" :key="link.text" link router :to="link.route">
            <v-icon>{{ link.icon }}</v-icon>
            <v-tab >{{ link.text }}</v-tab>
            </v-tab>
        <v-btn color="teal" elevation="8">
            <span >Sign Out</span>
            <v-icon right>mdi-logout</v-icon>
        </v-btn>
    </v-toolbar>

    <v-navigation-drawer app v-model="drawer" class="teal" dark absolute temporary>

        <v-row wrap>
            <v-col>
                <v-card class="text-center ma-1">
                    <v-responsive class="pt-4">
                        <v-avatar size="80">
                            <router-link to="/">
                            <img class="text-center" src="/avatar-1.png">
                            </router-link>
                        </v-avatar>
                    </v-responsive>
                    <v-card-text>
                        <p class="white--text subheading mt-1">Pratik Ni</p>

                        <v-dialog v-model="dialog" transition="dialog-top-transition" max-width="600">
                            <template v-slot:activator="{ on, attrs }">
                                <v-btn small class="pa-3 black" v-bind="attrs" v-on="on" >
                                    <!-- <v-icon small left>mdi-person_search</v-icon> -->
                                    <span>Add new Project</span>
                                </v-btn>
                            </template>
                            <template>
                                <v-card>
                                    <v-toolbar color="teal" dark >ADD PROJECT</v-toolbar>
                                    <v-card-text>
                                        <v-alert :value="Salert" type="success" class="mt-5" dark transition="scale-transition">
                                            Successfully Added
                                        </v-alert>
                                        <v-alert :value="Falert" type="error" class="mt-5" dark transition="scale-transition">
                                            Failed to add
                                        </v-alert>
                                                    <!--  -->
                                        <v-form ref="form">
                                            <v-text-field label="Title" v-model="title" :rules="inputRules"></v-text-field>
                                            <v-textarea label="Information" v-model="info" :rules="inputRules"></v-textarea>
                                            <v-menu :close-on-content-click="false" :nudge-right="40"  transition="scale-transition" offset-y
                                                min-width="auto" >
                                                <template v-slot:activator="{ on, attrs }">
                                                    <v-text-field v-model="date" label="Due date" prepend-icon="mdi-calendar" readonly
                                                        v-bind="attrs" v-on="on" :rules="inputRules" >
                                                    </v-text-field>
                                                </template>
                                                <v-date-picker v-model="date"></v-date-picker>
                                            </v-menu>
                                        </v-form>
                                                    <!--  -->
                                    </v-card-text>
                                    <v-card-actions class="justify-end">
                                        <v-btn text @click="submit">Add</v-btn>
                                        <v-btn text @click="close">Close</v-btn>
                                    </v-card-actions>
                                </v-card>
                            </template>
                        </v-dialog>

                    </v-card-text>
                </v-card>
            </v-col>
        </v-row>
        
        <v-list dense class="my-2">
            <v-list-item v-for="link in links" :key="link.text" link router :to="link.route" >
                <v-list-item-icon>
                    <v-icon>{{ link.icon }}</v-icon>
                </v-list-item-icon>

                <v-list-item-content>
                    <v-list-item-title>{{ link.text }}</v-list-item-title>
                </v-list-item-content>
            </v-list-item>
        </v-list>
    </v-navigation-drawer>
</nav>
</template>
 


<script>
export default {
     data() {
    return {
      drawer: false,
      links: [
        {icon: 'mdi-view-dashboard', text: 'Dashboard', route: '/' },
        {icon: 'mdi-code-braces', text: 'Projects', route: '/Projects' },
        {icon: 'mdi-account-group-outline', text: 'Team', route: '/Team' }
      ],
      dialog: false,
      title:'',
      info:'',
      date:'',
      Salert: false,
      Falert: false,
      inputRules: [
          v => v.length >= 3 || "minimum length is 3"
      ]
    }
  },
  methods: {
      submit() {
          
          if(this.$refs.form.validate()){
              this.Salert=true
              this.Falert=false
              console.log(this.title, this.info, this.date)
          }
          else{

              this.Salert=false
              this.Falert=true
              this.title=''
              this.info=''
              this.date=''
          }
      },
      close(){
            this.dialog=false
            this.Salert=false
            this.Falert=false
            this.title=''
            this.info=''
            this.date=''
        }
  }
}
</script>

