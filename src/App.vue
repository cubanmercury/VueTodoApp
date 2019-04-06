<template>
    <div id="app">
        <Header />
        <router-view/>
    </div>
</template>

<script>
import Header from './components/layout/Header';
export default {
    name: "App",
    components: {
        Header
    }
}
</script>




<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body{
  font-family: 'Bai Jamjuree', sans-serif;
  font-size: 16px;
  line-height: 1.4;
}
.btn{
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
  border-radius: 5px;
}
.btn:hover{
  background: #666;
}
#app{
  display: flex;
  flex-flow: column nowrap;
  align-items: center;
  width: 100%;
}
.todo-container{
  display: flex;
  flex-flow: column nowrap;
  align-items: center;
  width: 40%;
  height: auto;
}

</style>
