<template>
    <div id="main-container">
        <p>componente de msg</p>
        <div>
            <form id="burger-form">
                <div class="input-container">
                    <label for="nome">Nome do Cliente</label>
                    <input type="text" name="nome" 
                    id="nome"
                    v-model="nome"
                    placeholder="Digite seu nome">
                </div>
                <div class="input-container">
                    <label for="pao">Escolha o pão</label>
                    <select name="pao" id="pao"
                    v-model="pao">
                    <option value="">Selecione o pão</option>
                    <option value="integral">Integral</option>
                    </select>
                </div>
                <div class="input-container">
                    <label for="carne">Escolha a carne do seu burger</label>
                    <select name="carne" id="carne"
                    v-model="carne">
                    <option value="">Selecione oa carne</option>
                    <option value="maminha">Maminha</option>
                    </select>
                </div>
                <div class="input-container" id="opcionais-container">
                    <label id="opcionais-title" for="opcionais">Selecione os opcionais</label>
                    <div class="checkbox-container">
                        <input type="checkbox" name="opicionais" v-model="opicionais" value="salame">
                        <span>Salame</span>
                    </div>
                    <div class="checkbox-container">
                        <input type="checkbox" name="opicionais" v-model="opicionais" value="salame">
                        <span>Salame</span>
                    </div>
                    <div class="checkbox-container">
                        <input type="checkbox" name="opicionais" v-model="opicionais" value="salame">
                        <span>Salame</span>
                    </div>
                </div>
                <div class="input-container">
                    <input type="submit" value="Enviar meu burger" class="submit-btn">
                </div>
            </form>
        </div>
    </div>
</template>
<script>
export default {
    name: "Formburger",
    data() {
        return {
            nome:"fulano"
        }
    }
}
</script>
<style scoped>
#burger-form {
max-width: 400px;
margin: 0 auto;

}
.input-container {
display: flex;
flex-direction: column;
margin-bottom: 20px;
}
label {
    font-weight: bold;
    margin-bottom: 15px;
    color: #222;
    padding: 5px 10px;
    border-left: 4px solid #fcba03;
}
.input-container input ,
.input-container select {
padding: 5px 10px;
width: 300px;
}
#opcionais-container {
    flex-direction: row;
    flex-wrap: wrap;
}
#opcionais0title {
    width: 100%;
}
.checkbox-container {
    display: flex;
    align-items: flex-start;
    width: 50%;
    margin-bottom: 20px;
}
.checkbox-container span,
.checkbox-container input {
    width: auto;
}
.checkbox-container span{
    margin-left: 6px;
    font-weight: bold;
}
.submit-btn {
background-color: #222;
color:#fcba03;
font-weight: bold;
border: 2px solid #222;
padding: 10px;
font-size: 16px;
margin: 0 auto;
cursor: pointer;
transition: .5s;
}
.submit-btn:hover {
    background-color: transparent;
    color: #222;
}
</style>