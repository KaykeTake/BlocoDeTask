<template>
    <input type="button" @click="enviar" id="botao" value="SAVE">
</template>
<script>
export default{
    name: "BotaoTask",
    methods:{
        //enviando a confimação da ação de click no button para seu componente pai
        enviar(){
            this.$emit('receber', 'clicado')
        }
    }
}

</script>
<style scoped>
    #botao{
        background-color: #00DEE1;
        color: black;
        cursor: pointer;
        font-weight: bolder;
        width: 167px;
        height: 30px;
    }
</style>