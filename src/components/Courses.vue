<template>
    <div id="courses-container" class="tab" :class="{active: isActive}">
        <h1 class="title">Courses</h1>
        <table id="courses">
            <thead>
            <tr>
                <th>#</th>
                <th>Course Title</th>
                <th>Semester</th>
                <th>Grade</th>
            </tr>
            </thead>
            <tbody>
            <tr v-for="(course, index) in courses" :key="index">
                <td>{{index+1}}</td>
                <td>{{course.title}}</td>
                <td>{{course.semester}}</td>
                <td>{{course.grade}}</td>
            </tr>
            </tbody>
        </table>
        <br>
        <br>
        <div>
            <button @click='toggle = !toggle' id="add-course-button" class="blue-button">+</button>
            <span v-show='toggle'>
                <input class="input" type="text" v-model="title" id="title" placeholder="Course title">
                <input class="input" type="number" v-model="semester" min="1" max="8" placeholder="Semester" id="semester">
                <input class="input" type="number" v-model="grade" min="0" max="100" placeholder="Grade" id="grade">
                <button v-on:click="add_button" class="green-button" id="save-course">Save</button>
                <button @click='toggle = !toggle' class="grey-button" id="cancel-course">Cancel</button>
            </span>
        </div>
    </div>
</template>

<script>

    import Course from "../models/Course";
    import Profile from "./Profile";

    export default {
        el: '#add-course',
        name: "Courses",
        data: () => {
            return {
                toggle:false,
                isActive: false,
                title: "",
                semester: "",
                grade: "",
                courses: [
                    new Course("Agile Software development",1,82),
                    new Course("System modeling",1,85),
                    new Course("Object-oriented programming",2,99),
                    new Course("Estonian language Level A2",2,65)
                ]
            }
        },
        methods: {
            toggleCourses: function () {
                this.isActive = !this.isActive;
            },
            add_button: function () {
                let title = this.title;
                let semester = this.semester;
                let grade = this.grade;

                this.title = "";
                this.semester = "";
                this.grade = "";

                this.toggle = false;

                this.courses.push(new Course(title, semester, grade));
                this.computeGPA();
            },
            computeGPA: function () {
                var grade = 0;
                var points = 0;
                for (let i = 0; i < this.courses.length; i++) {
                    grade = this.courses[i].grade;
                    var point = 0;
                    if (grade > 90) {
                        point = 4;
                    }
                    else if (grade > 80) {
                        point = 3;
                    }
                    else if (grade > 70) {
                        point = 2;
                    }
                    else if (grade > 60) {
                        point = 1;
                    }
                    else if (grade > 50) {
                        point = 0.5;
                    }
                    else if (grade <= 50) {
                        point = 0;
                    }
                    points += point;
                }
                var NewGpa = points/this.courses.length;
                NewGpa = Math.round(NewGpa * 100) / 100;
                this.$props.add(NewGpa);
            }
        },
        props: {
            add: Function
        }
    }
</script>

<style scoped>

    .tab {
        display: none;
    }

    .tab.active {
        display: block;
    }

    table {
        width: 100%;
        border-collapse: collapse;

    }

    table th {
        padding: 8px 12px;
        text-align: left;
        border: 1px solid #cbcbcb;
        background-color: #03A9F4;
        color: #ffffff;
    }

    table td {
        padding: 8px 12px;
        border: 1px solid #cbcbcb;
    }

    .blue-button {
        background-color: #2196F3;
        color: #ffffff;
        border: none;
        padding: 10px 20px;
    }

    .green-button {
        background-color: #69f378;
        color: #ffffff;
        border: none;
        padding: 10px 10px;
    }

    .grey-button {
        background-color: #e1e8e6;
        color: #ffffff;
        border: none;
        padding: 10px 20px;
    }

    .input {
        border: 1px solid #cccccc;
        padding: 10px 20px;
        min-width: 135px;
    }

    #add-course {
        display: none;
    }

</style>