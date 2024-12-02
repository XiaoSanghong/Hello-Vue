<template>
  <div class="about">
    <center>
      <v-img alt="Vue logo" src="../assets/logo.png" style="width: 100px;"/>
    </center>
    <h1>This is an about page</h1>
    <v-btn color="primary" size="x-large" @click="handleCallParent">Call To Parent</v-btn>
    <v-row>
      <v-col cols="12" md="6" sm="6">
        <v-text-field v-model="studentObj.fname" placeholder="First Name"></v-text-field>
      </v-col>
      <v-col cols="12" md="6" sm="6">
        <v-text-field v-model="studentObj.lname" placeholder="last Name"></v-text-field>
      </v-col>
      <v-col cols="12" md="12" sm="12" style="text-align: center;">
        <h1>Full Name : {{ upperstring(fullName) }}</h1>
        <h1 style="color: red;">{{ message }}</h1>
      </v-col>
    </v-row>
  </div>
</template>

<script>
import myMix from '@/mixins/my-mix.vue';

  export default {
    name: "AboutPage",
    mixins: [myMix],
    props: {
        fname: String,
    },
    data() {
      return {
        studentObj: {fname: "", lname: "",},

        message: "",
      }
    },
    computed: {
      fullName() {
        return this.studentObj.fname + " " + this.studentObj.lname; 
      }
    },
    created () {
      this.studentObj.fname = this.fname;
    },
    watch: {
      "studentObj.fname"(doc, old) {
        //if(doc.length<3){
        //   this.message="Condition not Met";
        // }else{
        //   this.message="";
          
          this.message = (doc || "").length < 3 ? "Condition not Met" : "";
        //}
      }
    },
    methods: {
      
      handleCallParent(){
        let vm = this;
        vm.$emit("saveToChild", this.studentObj.fname);
      }
    },
  };
</script>

<style lang="scss" scoped>

</style>