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
  methods: {
    consoleLog(){
      console.log("Olá, estou editando através do gitHub")
    }
  }
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
</style>
