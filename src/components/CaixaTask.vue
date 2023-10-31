<template>
    <div class="oi">
        <input type="text" v-model='task' placeholder="Insira a tarefa">
        <!-- recebendo o os dados do componente filho e enviado para a função mencionada -->
        <BotaoTask @receber="evento"/>
    </div>
</template>

<script>
import BotaoTask from "./BotaoTask.vue";
export default{
    name: "CaixaTask",

    components:{
        BotaoTask
    },
    data(){
        return{
            task: '',
        }
    },
    methods: {
         /*aqui a função evento está executando a captura da ação do clique no button  do componente
         filho e fazendo também a captura dos dados da vareável "task" e enviado pro seu componente pai
        */
        evento(data){
            if(data === 'clicado'){
                this.$emit('receber', this.task)
            }
        }
  }
}
</script>

<style scoped>
</style>