<template>
    <div class="oi">
        <!-- recebendo o os dados do componente filho e enviado para a função mencionada -->
        <CaixaTask @receber="evento"/>
        <!-- Um loop criado usando v-for com o intuito de exibir as tasks no array "tasks" -->
        <div class='task' v-for="task in tasks" :key="task.id">
            <p>{{ task.task }}</p>
        </div>
    </div>
</template>
<script>
import CaixaTask from "./CaixaTask.vue";

export default{
    name: 'MuralTask',
    components: {
        CaixaTask,
    },
    data(){
        return{
            tasks: [],
        }
    },
    methods:{
        /*aqui a função evento está executando a captura dos dados so seu filho CaixaTask
        e inserindo o mesmo no array "tasks"
        */
        evento(data){
            this.tasks.push({
                task: data
            })
        }
    }
}
</script>
<style scoped></style>