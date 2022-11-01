<template>
  <div id="app">
    <header>MINHAS TAREFAS</header>
    <Tarefas />
  </div>
</template>

<script>
import Tarefas from "./components/Tarefas";
export default {
  name: "App",
  components: {
    Tarefas,
  },
};
</script>

<style scoped>
header {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 80px;
  font-size: 40px;
  color: #fff;
  text-shadow: 3px 2px 7px #000000;
}

header:hover {
  color: #fff;
  text-shadow: #fff 0px 0px 5px, #fff 0px 0px 10px, #fff 0px 0px 15px,
    #fff 0px 0px 20px, #fff 0px 0px 30px, #fff 0px 0px 40px, #fff 0px 0px 50px,
    #fff 0px 0px 75px, 3px 2px 0px rgba(0, 0, 0, 0);
  transition: all 1s;
}
</style>
