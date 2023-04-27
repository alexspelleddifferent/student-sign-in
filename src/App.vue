<template>
  <div id="app">
    <new-student-form v-on:student-added="newStudentAdded"></new-student-form>
    <student-table v-bind:students="students"></student-table>
    <student-message></student-message>
  </div>
</template>

<script>
import NewStudentForm from './components/NewStudentForm.vue';
import StudentMessage from './components/StudentMessage.vue';
import StudentTable from './components/StudentTable.vue';

export default {
  name: 'App',
  components: {
    NewStudentForm,
    StudentMessage,
    StudentTable
  },
  data() {
    return {
      students:[]
    }
  },
  methods: {
    newStudentAdded(student) {
      this.students.push(student)
      this.students.sort(function(s1, s2) {
        return s1.name.toLowerCase() < s2.name.toLowerCase() ? -1:1
      })
    }
  }
}
</script>

<style>
@import "https://cdn.jsdelivr.net/npm/bootstrap@4.6.0/dist/css/bootstrap.min.css"
</style>
