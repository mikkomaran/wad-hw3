<template>
    <footer>
        <ul class="links">
            <li>
                <a href="https://ois2.ut.ee/" target="_blank">OIS</a>
            </li>
            <li>
                <a href="https://courses.cs.ut.ee/" target="_blank">Courses</a>
            </li>
        </ul>
    </footer>
</template>

<script>
    export default {
        name: "Footer"
    }
</script>

<style scoped>

    footer {
        padding: 30px 0;
        background-color: #607D8B;
        margin-top: 10px;
        height: 100px;
        position: absolute;
        bottom: 0;
        width: 100%;
    }

    footer .links {
        display: block;
        width: 100%;
        max-width: 200px;
        margin: 0 auto;
        color: #acd7ff;
        font-size: 14px;
    }

    footer .links a {
        text-decoration: none;
        color: #acd7ff;
    }

    footer .links a:hover {
        text-decoration: underline;
        color: #337aff;
    }

</style>