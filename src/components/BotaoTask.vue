<template>
    <input type="button" @click="enviar" value="Save">
</template>
<script>
export default{
    name: "BotaoTask",
    methods:{
        //enviado a confimação da ação de click no button para seu componente pai
        enviar(){
            this.$emit('receber', 'clicado')
        }
    }
}

</script>
<style scoped></style>