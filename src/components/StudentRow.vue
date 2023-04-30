<template>
    <tr v-bind:class="{present:student.present, absent:!student.present}">
        <td>{{ student.name }}</td>
        <td>{{ student.starID }}</td>
        <td> <input type="checkbox" v-bind:checked="student.present" v-on:change="AorL(student, $event.target.checked)"></td>
        <td v-show="edit"> <img v-on:click="deleteStudent" src="@/assets/delete.png"> </td>
    </tr>
</template>

<script>
export default {
    name: 'StudentRow',
    emits: ['student-arrived-or-left', 'delete-student'],
    props: {
        student: Object,
        edit: Boolean
    },
    methods: {
        AorL(student, present) {
            this.$emit('student-arrived-or-left', student, present)
        },
        deleteStudent() {
            this.$emit('delete-student', this.student)
        }
    }
}
</script>

<style scoped>
.present {
    color: gray;
    font-style: italic;
}

.absent {
    color: black;
    font-weight: bold;
}

img {
    height:25px;
}
</style>