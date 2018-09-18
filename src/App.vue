<template>
    <div id="papp">


        <nav>
            <div class="nav-wrapper">
                <a href="#" class="brand-logo">Logo</a>
                <ul id="nav-mobile" class="right hide-on-med-and-down">
                    <li><router-link to="/">Home</router-link> |</li>
                    <li><router-link to="/about">About</router-link></li>
                </ul>
            </div>
        </nav>

        <router-view/>
    </div>
</template>

<script>
    export default {
        name: "App"
    }
</script>


<style lang="scss">
    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
    }
    /*#nav {*/
        /*padding: 30px;*/
        /*a {*/
            /*font-weight: bold;*/
            /*color: #2c3e50;*/
            /*&.router-link-exact-active {*/
                /*color: #42b983;*/
            /*}*/
        /*}*/
    /*}*/
</style>