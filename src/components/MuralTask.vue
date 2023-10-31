<template>
    <div class="container">
        <!-- recebendo o os dados do componente filho e enviado para a função mencionada -->
        <CaixaTask @receber="evento"/>
        <!-- Um loop criado usando v-for com o intuito de exibir as tasks no array "tasks" -->
        <div class="boxx">
            <div class="boxmain">
                <draggable classe='draggable' v-model="tasks"  group="people" @start="drag=true" @end="drag=false">
                    <div class="box" v-for="(task, index) in tasks" :key="task.id">
                        <div class='task'>
                            <p>{{ task.task }}</p>
                        </div>  
                        <a href="#" class="excluir" v-on:click.prevent='excluir(index)'>excluir</a>
                    </div>
                </draggable>
            </div>
        </div>
    </div>
</template>

<script>
import CaixaTask from "./CaixaTask.vue";
import draggable from 'vuedraggable';
export default{
    name: 'MuralTask',
    components: {
        CaixaTask,
        draggable
    },
    data(){
        return{
            tasks: [],
        }
    },
    mounted(){
        this.carregamento()
    },
    watch: {
        tasks(){
            this.alteracao()
        }
    },
    methods:{
        carregamento(){
            //Setando na array "tasks" a array armazenada no localStorage
            this.tasks = JSON.parse(localStorage.getItem('tasks')) || [];
        },
        //Função para exlusão da atividade
        excluir(index){
            this.tasks.splice(index,1)
            //setando no localStorage a atualização de excluimento de um card 
            localStorage.setItem('tasks', JSON.stringify(this.tasks));
        },
        alteracao(){
            localStorage.setItem('tasks', JSON.stringify(this.tasks));
        },
        /*aqui a função evento está executando a captura dos dados so seu filho CaixaTask
        e inserindo o mesmo no array "tasks"
        */
        evento(data){
            if (data.trim() == ''){
                return
            }
            this.tasks.unshift({
                task: data
            })
        //setando o array "tasks" no localStorage no formato de string com a key 'tasks'
            localStorage.setItem('tasks', JSON.stringify(this.tasks));
        }
    }
}
</script>
<style scoped>
    .boxx{
        display: flex;
        justify-content: center;
        height: 400px;
    }
    .boxmain{
        margin-top: 20px;
        display: flex;
        flex-wrap: wrap;
        justify-content: center;
        width: 200px;
        overflow: auto;
    }
    .box{
        border: 2px solid black;
        word-break: break-word;
        margin-top: 10px;
        width: 180px;
        height: min-content;
        background-color: white;
        border-radius: 2%;
    }
    .task{
        text-align: left;
        font-weight: bold;
        margin-left: 5px;
    }
    .excluir{
        margin-left: 4px;
        text-decoration: none;
        color: red;
        font-size: 10px;
    }
</style>