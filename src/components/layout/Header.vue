<template>
    <header class="header">
        <h1>TodoList</h1>
        <div id="nav">
            <router-link to='/'>Home</router-link>
            <router-link to='/about'>About</router-link>
        </div>
    </header>
</template>

<script>
export default {
    name: "header"
}
</script>

<style>
.header{
    background: #333;
    color: #fff;
    text-align: center;
    padding: 10px;
    width: 100%;
}
.header a{
    color: #fff;
    padding-right: 5px;
    margin-right: 5px;
    text-decoration: none;
}
#nav>a:first-of-type{
    border-right: 1px solid #fff;
}

</style>
