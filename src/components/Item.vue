<template>
  <div id="item">
    <ul>
      <li v-for="itens in lista" :key="itens.key">
        <span>{{ itens.text }}</span>
        <button @click="deletarTarefa(itens.key)">Concluir</button>
        <span>Testando aplicação</span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Item",
  props: ["lista", "delete"],
  methods: {
    deletarTarefa(item) {
      this.delete(item);
    },
  },
};
</script>

<style scoped>
#item {
  white-space: pre-wrap;
  word-wrap: break-word;
}

ul {
  list-style: none;
  padding: 0;
  margin-top: 20px;
}

ul li {
  padding: 15px;
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
}

/*Vai aplicar em todos os filhos, com excessão do primeiro*/
li:not(:first-child) {
  border-top: 1px solid #eee;
}

span {
  color: #0d2636;
}

button {
  cursor: pointer;
  background: #ddd;
  border: 0;
  color: #000;
  padding: 8px 7px;
  outline: none;
  border-radius: 10px;
  font-size: 12px;
}
</style>
