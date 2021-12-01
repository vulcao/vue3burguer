<template>
    <div class="message-container">
        <p>{{ mensagem }}</p>
    </div>
</template>
<script>
export default {
    name: "Message",
    props: {
        mensagem: String
    }
}
</script>
<style scoped>
.message-container {
    color:#004085;
    background-color: #CCE5FF;
    border: 2px solid #BBDAFF;
    border-radius: 5px;
    padding: 10px;
    max-width: 400px;
    margin: 30px auto;
}
</style>