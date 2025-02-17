<template>
  <div>
    <h2>Employee List</h2>
    <p v-if="employees.length === 0">List is Empty</p>
    <table v-else border="1" class="employee-table">
      <thead>
        <tr>
          <th>Emp ID</th>
          <th>Name</th>
          <th>Email</th>
          <th>Skills</th>
          <th>Phone</th>
          <th>Gender</th>
          <th>DOB</th>
          <th>Actions</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(employee, index) in employees" :key="index">
          <td>{{ employee.empID }}</td>
          <td>{{ employee.name }}</td>
          <td>{{ employee.email }}</td>
          <td>{{ employee.skills }}</td>
          <td>{{ employee.phone }}</td>
          <td>{{ employee.gender }}</td>
          <td>{{ employee.dob }}</td>
          <td>
            <button @click="$emit('edit-employee', index)">Edit</button>
            <button @click="$emit('delete-employee', index)">Delete</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  props: {
    employees: Array,
  },
  methods: {
    editMode(index) {
      this.employees[index].isEditing = true;
    },
    saveEdit(index) {
      this.$emit("edit-employee", { index, updatedEmployee: this.employees[index] });
      this.employees[index].isEditing = false;
    },
  },
};
</script>

<style>
.input-field {
  display: block;
  width: 60%;
  padding: 10px;
  margin-bottom: 10px;
}

.employee-table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 10px;
}

.employee-table th, .employee-table td {
  padding: 10px;
  text-align: left;
}
</style>
