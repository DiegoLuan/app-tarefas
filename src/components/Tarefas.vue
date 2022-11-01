<template>
  <div id="task">
    <form @submit.prevent="addTarefa">
      <input type="text" placeholder="Tarefas de hoje?" v-model="tarefa" />
      <button type="submit">Adicionar</button>
    </form>

    <Item :lista="deveres" :delete="deleteTask" />

    <!-- Só vai aplicar a classe 'pend' se a variavel 'pendente' for true -->
    <span v-show="deveres != ''"
      >Você tem
      <strong :class="{ pend: pendente }">{{ deveres.length }}</strong> tarefas
      pendentes
    </span>
  </div>
</template>

<script>
import Item from "./Item";
export default {
  name: "Tarefas",
  components: {
    Item,
  },
  data() {
    return {
      tarefa: "",
      deveres: [],
      item: "",
      pendente: false,
    };
  },
  methods: {
    addTarefa() {
      if (this.tarefa) {
        this.deveres.push({
          text: this.tarefa,
          key: Date.now(),
        });
      } else if (this.tarefa == "") {
        alert("Digite alguma tarefa...");
      }

      this.tarefa = "";
    },
    deleteTask(key) {
      let filtro = this.deveres.filter((item) => {
        return item.key !== key;
      }); //retornar todos os elementos que tem a key diferente da key que foi passado como parametro ao clicar no botão concluir

      return (this.deveres = filtro);
    },
  },
  watch: {
    deveres: {
      //toda vez que o data 'deveres' sofrer alguma alteração, vai chamar o método 'handler'
      deep: true,
      handler() {
        localStorage.setItem("tasks", JSON.stringify(this.deveres));
        this.deveres.length > 4
          ? (this.pendente = true)
          : (this.pendente = false);
      },
    },
  },
  created() {
    // É chamado automaticamente após a instancia do vueJs ser criada
    const json = localStorage.getItem("tasks");
    this.deveres = JSON.parse(json) || []; //se não tiver nenhum item, vai passar um array vazio!
  },
};
</script>

<style scoped>
#task {
  max-width: 700px;
  background: #fff;
  border-radius: 5px;
  padding: 20px;
  margin: 20px auto;
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.3);
}

form {
  margin-top: 30px;
  display: flex;
  flex-direction: row;
}

form button {
  cursor: pointer;
  background: #0f5959;
  border: 0;
  border-radius: 10px;
  margin-left: 5px;
  padding: 0 15px;
  display: flex;
  justify-content: center;
  align-items: center;
  color: #fff;
  font-weight: 500;
}

form button:hover {
  border: 1px solid #0f5959;
  background: #fff;
  color: #000;
  transition: all 1s;
}

input {
  flex: 1; /*Pegar todo restante da tela */
  border: 1px solid #eee;
  padding: 6px 10px;
  border-radius: 10px;
  font-size: 14px;
  outline: none; /*tirar bordar quando clicar*/
}

span {
  font-size: 14px;
}

.pend {
  color: red;
}
</style>

