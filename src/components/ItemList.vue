<!-- <template>
<div>
    <h1>List of items</h1>
   <ul>
    <li v-for="(item, index) in items" :key="index">
        {{ item }}
        <button @click="deleteItem(index)">Delete</button>
    </li>
   </ul>
</div>
</template>
<script>
export default {
    props: {
        items: Array,
    },
    methods: {
            deleteItem(index) {
                this.$emit("delete-item", index);
            }
        }
}
</script> -->

<!-- 
<div>
    <h2>Create Employee</h2>
    <form @submit.prevent="submitForm">
      <input v-model="employee.empID" placeholder="Emp ID" required class="input-field"/>
      <input v-model="employee.email" placeholder="Email ID" required class="input-field"/>
      <input v-model="employee.name" placeholder="Name" required class="input-field"/>
      <input v-model="employee.skills" placeholder="Skills" required class="input-field"/>
      <input v-model="employee.phone" placeholder="Phone Number" required class="input-field"/>
      <select v-model="employee.gender" required class="input-field">
        <option value="Male">Male</option>
        <option value="Female">Female</option>
      </select>
      <input v-model="employee.dob" type="date" required class="input-field"/>
      <button type="submit">Create</button>
    </form>
  </div> -->
  <template>
    <div>
      <h2>Create Employee</h2>
      <form @submit.prevent="submitForm">
        <input v-model="employee.empID" placeholder="Emp ID"  class="input-field"/>
        <input v-model="employee.email" placeholder="Email ID"  class="input-field"/>
        <input v-model="employee.name" placeholder="Name"  class="input-field"/>
        <input v-model="employee.skills" placeholder="Skills"  class="input-field"/>
        <input v-model="employee.phone" placeholder="Phone Number"  class="input-field"/>
        <select v-model="employee.gender"  class="input-field">
          <option value="Male">Male</option>
          <option value="Female">Female</option>
        </select>
        <input v-model="employee.dob" type="date" required class="input-field"/>
        <button type="submit">{{ isEditing ? 'Update' : 'Create' }}</button>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      editingEmployee: Object,
    },
    data() {
      return {
        employee: this.editingEmployee || {
          empID: "",
          email: "",
          name: "",
          skills: "",
          phone: "",
          gender: "",
          dob: "",
        },
      };
    },
    computed: {
      isEditing() {
        return this.editingEmployee !== null;
      }
    },
    methods: {
      submitForm() {
        this.$emit("add-employee", { ...this.employee });
        this.employee = { empID: "", email: "", name: "", skills: "", phone: "", gender: "", dob: "" };
      },
    },
  };
  </script>
  
  <style>
  .input-field {
    display: block;
    width: 100%;
    padding: 10px;
    margin-bottom: 10px;
  }
  </style>