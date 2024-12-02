<template>
  <div class="home">
    <h1>My Home page</h1>
    <ul>
      <li v-for="(color,ind) in colorList" :key="ind" :style="'color:'+color">{{ color }}</li>
    </ul>
     <v-img alt="Vue logo" src="../assets/logo.png" style="width: 100px;"/>
    <HelloWorld msg="Welcome to Your Vue.js App" />  
    <h1 v-show="studentName">Student Name</h1>
    <center>
      <table border="1">
        <thead>
          <tr>
            <th>ID</th>
            <th>Name</th>
            <th>Phone Number</th>
            <th>Action</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="stDoc in studentList"
          :key="stDoc.id"
          
          >
          <td>{{ stDoc.id }}</td>
          <td>{{ stDoc.name }}</td>
          <td>{{ stDoc.phoneNumber }}</td>
          <td><v-btn class="primary" @click="clickonrow(stDoc)">Show</v-btn></td>
          </tr>
        </tbody>
      </table>
    </center>
    <AboutPage v-if="studentName" :fname="studentName" @saveToChild="callFromChild"></AboutPage>
    <ProductView>

    </ProductView>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import ProductView from '@/views/ProductView.vue'
import AboutPage from '@/views/AboutView.vue'
export default {
  name: 'HomeView',

  components: {
    HelloWorld,
    ProductView,
    AboutPage,
  },
  data() {
    return {
      colorList: ["Red","Blue","Pink","Yellow"],
      studentList:[
        {id: "01", name:"Dara", phoneNumber:"012 424 541"},
        {id: "02", name:"Makara", phoneNumber:"032 512 252"},
        {id: "03", name:"Kanha", phoneNumber:"012 535 354"}
      ],
      studentName: "",
    };
  },
  methods: {
    clickonrow(doc) {
      let vm = this;
      vm.studentName = vm.studentName ? "" :doc.name;
    },
    callFromChild(doc){
      let vm = this;
      vm.studentName=doc;
    }
  },
//   data() {
//     return {
//       productList: [
//   {
//     _id: "aa",
//     name: "Room A",
//     desc: "BTB",
//     price: 20000,
//     category: "House",
//     status: true,
//     postDate: "2024-11-07",
//     type: "RealEstate",
//     page: "Home",
//     url: "https://images.pexels.com/photos/610293/pexels-photo-610293.jpeg",
//   },
//   {
//     _id: "bb",
//     name: "Room B",
//     desc: "PP",
//     price: 30000,
//     category: "Condo",
//     status: true,
//     postDate: "2024-11-07",
//     type: "RealEstate",
//     page: "Home",
//     url: "https://images.pexels.com/photos/3680219/pexels-photo-3680219.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
//   },
//   {
//     _id: "cc",
//     name: "Room B",
//     desc: "PP",
//     price: 30000,
//     category: "Condo",
//     status: true,
//     postDate: "2024-11-07",
//     type: "RealEstate",
//     page: "Home",
//     url: "https://images.pexels.com/photos/3680219/pexels-photo-3680219.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
//   },
//   {
//     _id: "dd",
//     name: "Room B",
//     desc: "PP",
//     price: 30000,
//     category: "Condo",
//     status: true,
//     postDate: "2024-11-07",
//     type: "RealEstate",
//     page: "Home",
//     url: "https://images.pexels.com/photos/3680219/pexels-photo-3680219.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
//   },
//   {
//     _id: "ee",
//     name: "Room B",
//     desc: "PP",
//     price: 30000,
//     category: "Condo",
//     status: true,
//     postDate: "2024-11-07",
//     type: "RealEstate",
//     page: "Home",
//     url: "https://images.pexels.com/photos/3680219/pexels-photo-3680219.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
//   },
//   {
//     _id: "ff",
//     name: "Room B",
//     desc: "PP",
//     price: 30000,
//     category: "Condo",
//     status: true,
//     postDate: "2024-11-07",
//     type: "RealEstate",
//     page: "Home",
//     url: "https://images.pexels.com/photos/3680219/pexels-photo-3680219.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
//   },
//   {
//     _id: "gg",
//     name: "Room B",
//     desc: "PP",
//     price: 30000,
//     category: "Condo",
//     status: true,
//     postDate: "2024-11-07",
//     type: "RealEstate",
//     page: "Home",
//     url: "https://images.pexels.com/photos/3680219/pexels-photo-3680219.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
//   },
//   {
//     _id: "hh",
//     name: "Room B",
//     desc: "PP",
//     price: 30000,
//     category: "Condo",
//     status: true,
//     postDate: "2024-11-07",
//     type: "RealEstate",
//     page: "Home",
//     url: "https://images.pexels.com/photos/3680219/pexels-photo-3680219.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
//   },
//   {
//     _id: "ii",
//     name: "Room B",
//     desc: "PP",
//     price: 30000,
//     category: "Condo",
//     status: true,
//     postDate: "2024-11-07",
//     type: "RealEstate",
//     page: "Home",
//     url: "https://images.pexels.com/photos/3680219/pexels-photo-3680219.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
//   },
//   {
//     _id: "jj",
//     name: "Room B",
//     desc: "PP",
//     price: 30000,
//     category: "Condo",
//     status: true,
//     postDate: "2024-11-07",
//     type: "RealEstate",
//     page: "Home",
//     url: "https://images.pexels.com/photos/3680219/pexels-photo-3680219.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
//   },
//   {
//     _id: "kk",
//     name: "Room B",
//     desc: "PP",
//     price: 30000,
//     category: "Condo",
//     status: true,
//     postDate: "2024-11-07",
//     type: "RealEstate",
//     page: "Home",
//     url: "https://images.pexels.com/photos/3680219/pexels-photo-3680219.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
//   },
//   {
//     _id: "ll",
//     name: "Room B",
//     desc: "PP",
//     price: 30000,
//     category: "Condo",
//     status: true,
//     postDate: "2024-11-07",
//     type: "RealEstate",
//     page: "Home",
//     url: "https://images.pexels.com/photos/3680219/pexels-photo-3680219.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1",
//   },
// ];
//     }
//   },
}
</script>
