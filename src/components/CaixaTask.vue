<template>
    <div class="container">
        <div class="box">
            <textarea id="task" v-model='task'
            placeholder="Write a task"
            @keydown.enter.exact.prevent="enter">
            </textarea>
        </div>
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
         //função que executa o input de text utilizando a tecla ENTER do teclado
        enter(){
            this.$emit('receber', this.task)
            this.task = ''
        },
        /*aqui a função evento está executando a captura da ação do clique no button  do componente
         filho e fazendo também a captura dos dados da vareável "task" e enviado pro seu componente pai
        */
        evento(data){
            if(data === 'clicado'){
                this.$emit('receber', this.task)
            }
            this.task = ''
        }
  }
}
</script>

<style scoped>
    #task{
        border-color: black;
        outline:none;
        resize: none;
    }
</style>