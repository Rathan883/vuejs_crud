
<template>
    <div>
      <h2>Create Employee</h2>
      <form @submit.prevent="submitForm">
        <input v-model="employee.empID" placeholder="Emp ID" required />
        <input v-model="employee.email" placeholder="Email ID" required />
        <input v-model="employee.name" placeholder="Name" required />
        <input v-model="employee.skills" placeholder="Skills" required />
        <input v-model="employee.phone" placeholder="Phone Number" required />
        <select v-model="employee.gender" required>
          <option value="Male">Male</option>
          <option value="Female">Female</option>
        </select>
        <input v-model="employee.dob" type="date" required />
        <button type="submit">Create</button>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        employee: {
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
    methods: {
      submitForm() {
        this.$emit("add-employee", { ...this.employee });
        this.employee = { empID: "", email: "", name: "", skills: "", phone: "", gender: "", dob: "" };
      },
    },
  };
  </script>