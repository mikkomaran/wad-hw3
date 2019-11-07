<template>
    <main id="app">
        <Header></Header>
        <section id="container">
            <section id="main">
                <div class="content">
                    <Profile ref="profile"/>
                    <Courses ref="courses"/>
                </div>
                <Controls @togglePage="togglePage"/>
            </section>
        </section>
        <Footer />
    </main>
</template>

<script>

    import Header from "./components/Header";
    import Footer from "./components/Footer";
    import Profile from "./components/Profile";
    import Courses from "./components/Courses";
    import Controls from "./components/Controls";
    export default {
        name: 'app',
        components: {
            Controls,
            Courses,
            Profile,
            Footer,
            Header
        },
        props: {

        },
        methods: {
            togglePage: function () {
                this.$refs.profile.toggleProfile();
                this.$refs.courses.toggleCourses();
            }
        },

    }

</script>

<style>
    * {
        box-sizing: border-box;
        font-family: 'Livvic', sans-serif;
    }

    html, body {
        padding: 0;
        margin: 0;
        width: 100%;
        height: 100%;
        background-color: #eaeaea;
    }

    main {
        position: relative;
        min-height: 100%;
        padding-bottom: 110px;
    }

    #container {
        width: 80%;
        max-width: 900px;
        min-width: 320px;
        padding: 15px;
        background-color: #ffffff;
        margin: 0 auto;
    }

    .content {
        padding: 10px;
        border: 1px solid #cbcbcb;
    }

</style>
