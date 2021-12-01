<template>
    <div :class="tipo">
        <p>{{ mensagem }}</p>
    </div>
</template>
<script>
export default {
    name: "Message",
    props: {
        mensagem: String,
        tipo: String
    }
}
</script>
<style scoped>
div {
    border-radius: 5px;
    padding: 10px;
    max-width: 400px;
    margin: 30px auto;
}
.azul {
    color:#004085;
    background-color: #CCE5FF;
    border: 2px solid #BBDAFF;
}
.vermelho {
    color:#850000;
    background-color: #ffe0cc75;
    border: 2px solid #d4d2d242;
}
.verde {
    color:#00851d;
    background-color: #ccffe7b7;
    border: 2px solid #bfd6c342;
}
</style>