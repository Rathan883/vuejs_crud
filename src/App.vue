<template>
  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
  <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
   
    <!-- <button  @click = "count++">{{ count }}</button>
    <div :style ="{color: textColor, fontSIze: computedFontSize + 'px'}" >Styled Text</div> -->
    <!-- <h2 ref = "title">This is a Vue App</h2> -->
<!-- 
    <div :class="{ active: isActive, 'text-bold': isBold}" class = "default">Hello Vue</div> -->
   
  <!-- <div>
    <p>computed: {{
      doubleComputed }}</p>
      <p>Method: {{ result }}</p>
      <button @click = "doubleMethod()">Increment</button>
  </div>

  <div>
    <p v-if = "count > 10">count is greater than 10</p>
      <p v-if-else-if="count > 5">count is greater than 5</p>
      <p v-else>Count is 5 or below</p>
    <h1>{{ count}} </h1>
    <button @click ="count++">Increment</button>
  </div>
  <div>
    <h2>Counter: {{  count }}</h2>
    <p>{{ message }}</p>
    <button @click = "increment">Increment</button>
    <button @click = "decrement">Decrement</button>"
  </div> -->
<!-- 
  <div>
    <h2>List of Fruits</h2>
    <ul>
      <li v-for = "(fruit, index) in fruits" :key="index"></li>
      {{  index + 1  }}.{{  fruit }}
    </ul>
    <ul>
      <li v-for="user in users" :></li>
    </ul>
  </div>

  <ChildComponent name ="Rathan" :userData="userData" /> -->

  <div>
    <!-- <h2>Users list</h2> -->
  <!-- <ItemList :items="items" @delete-item="deleteitem">

  </ItemList> -->
  <div>
    <h1>Employee Management</h1>
    <button @click="showList" :class="{ 'active-btn': showListContent }" class="toggle-btn">List</button>
    <button @click="showCreate" :class="{ 'active-btn': showCreateForm }" class="toggle-btn">Create</button>

    <EmployeeList v-if="showListContent" :employees="employees" @edit-employee="updateEmployee" @delete-employee="deleteEmployee" />
    <CreateForm v-if="showCreateForm" @add-employee="addEmployee" :editingEmployee="editingEmployee" />
    
    
  </div>
  </div>
  
</template>

<!-- <script>
import ItemList from './components/ItemList.vue';

export default{
  components: {
    ItemList
  },
  data() {
    return {
      items: ["Apple", "Banana", "Mango", "Orange"]
    };
  },
  methods:{
    deleteitem(index){
      this.items.splice(index, 1)
    }
  }
} -->
<!-- // export default {
//   data() {
//     return {
//       users: [
//         { id: 1, name: 'rathan', email:"rathanmogaveer@gmail.com"},
//         { id: 2, name: 'Akshay', email:"akshaydevadiga07@gmail.com"},
//         { id: 1, name: 'Deekshith', email:"deekshithkotegar7@gmail.com"},
//       ]
//     }
//   }
// } -->



<!-- 
// import HelloWorld from './components/HelloWorld.vue'
// import Home from './components/Home.vue'
// export default{
//   data(){
//     return{
//       count:1,
//       fontSize:20
//     };
//   },
//   computed:{
//     textColor(){
//       if(this.count >=5){
//         return 'red'
//       }
//       else{
//         return 'green'
//       }
//     }
  
//     },
//     computedFontSize(){
//       return this.count + this.fontSize;
    
//   }} -->
<!-- 
// export default{
//   data(){
//     return {
//       count: 0,
//       result : 0,
//     };
//   },
//   computed: {
//     doubleComputed(){
//       console.log("computed is running...");
//       return this.result * 2;
//     }
//   }
// }


  // export default{
  //   data() {
  //     return {
  //       isActive: true,
  //       isBold:true
  //     };
  //   }
  // }
  // export default{
  //   data(){
  //     return{
  //       count: 0,
  //       message: "Keep going"
  //     }
  //   },
  // methods:{
  //   increment()
  //     this.count++;
  //   },
  //   decremnt(){
  //     this.count--;
  //   }
  // }
  // },
  // watch:{
  //   count(newValue, oldValue){
  //     console.log(`count changed from ${oldValue} to ${newValue}`)
  //   }
  // }

  //  -->
  




<!-- 

// export default {
//   created(){
//     console.log("component Created from created");
    
//   },
//   mounted(){
//     console.log("component Created from mounted");
//   }
//   }; -->


<!-- </script> -->

<script>
import CreateForm from "./components/ItemList.vue";
import EmployeeList from "./components/EmployeeList.vue";

export default {
  components: {
    CreateForm,
    EmployeeList,
  },
  data() {
    return {
      employees: [],
      showCreateForm: false,
      showListContent: true,
      editingEmployee : {},
    };
  },
  methods: {
    addEmployee(employee) {
      this.employees.push(employee);
      this.showCreateForm = false;
      this.showListContent = true;
      

    },
    updateEmployee(index) {
      this.editingEmployee = { ...this.employees[index] };
      // console.log('testing ',this.editingEmployee.name)
      this.showCreateForm = true;
      this.showListContent = false;
    },
    deleteEmployee(index) {
      if (confirm("Are you sure you want to delete this employee?")) {
        this.employees.splice(index, 1);
      }
    },
    showCreate() {
      this.showCreateForm = true;
      this.showListContent = false;
      this.editingEmployee = null;
    },
    showList() {
      this.showCreateForm = false;
      this.showListContent = true;
    }, 
    showEdit(){
      this.showListContent = true;
    
    }
  },
};
</script>


<style>
/* .active {
  color :blue;}
  .text-biold {
    font-weight: bold;}
    .default{ background-color: greenYellow;} */
    
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

  .toggle-btn {
  padding: 10px;
  margin: 5px;
  border: none;
  cursor: pointer;
  background-color: white;
  color: black;
}

.active-btn {
  background-color: blue;
  color: white;
}

</style>
