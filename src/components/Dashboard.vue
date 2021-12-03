<template>
    <div class="burguer-table">
        <Message :mensagem="msg" :tipo="msgTipo" v-show="msg" />
        <div>
            <div id="burguer-table-heading">
                <div class="order-id">#:</div>
                <div>Cliente:</div>
                <div>Pão:</div>
                <div>Carne:</div>
                <div>Opcionais:</div>
                <div>Ações:</div>
            </div>
        </div>
        <div id="burguer-table-rows">
            <div class="burguer-table-row" v-for="burger in burgers" :key="burger.id">
                <div class="order-id">{{ burger.id }}</div>
                <div>{{ burger.nome }}</div>
                <div>{{ burger.pao }}</div>
                <div>{{burger.carne }}</div>
                <div>
                    <ul>
                        <li v-for="(opcional,index) in burger.opcionais" :key="index">
                            {{ opcional }}
                        </li>
                    </ul>
                </div>
                <div class="acoes">
                    <select name="status" class="status"
                    @change="updateBurger($event,burger.id)">
                        <option>Selecione</option>
                        <option v-for="statu in status" 
                        :key="statu.id" 
                        :value="statu.tipo"
                        :selected="burger.status == statu.tipo">
                            {{statu.tipo}}
                        </option>
                    </select>
                    <button class="delete-btn"
                    @click="deleteBurger(burger.id)">
                    Cancelar
                    </button>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import Message from "../components/Message"
export default{
    name: "Dashboard",
    components: {
        Message
    },
    data() {
        return {
            burgers: null,
            burger_id: null,
            status: [],
            msg: null,
            msgTipo: null
        }
    },
    methods: {
        async getPedidos() {
            const req = await fetch("http://localhost:3000/burgers");
            const data = await req.json();
            this.burgers = data;
        },
        async getStatus() {
            const req = await fetch("http://localhost:3000/status");
            const data = await req.json();
            this.status = data;
        },
        async deleteBurger(id) {
            console.log(id)
            const req = await fetch(`http://localhost:3000/burgers/${id}`,{
                method: "DELETE"
            });
            const res = await req.json();
            // mensagem
            this.msg = `Pedido nº ${id} foi cancelado`;
            this.msgTipo = "vermelho"
            setTimeout(() => this.msg = "",3000);
            // recarrega lista
            this.getPedidos();
        },
        async updateBurger(event,id){
            console.log(event)
            console.log(id)
            const option = event.target.value;
            const dataJson = JSON.stringify({ status: option });
            const req = await fetch(`http://localhost:3000/burgers/${id}`,{
                method: "PATCH",
                headers: { "Content-Type": "application/json" },
                body: dataJson
            });
            const res = await req.json();
            // mensagem
            this.msg = `Pedido nº ${id} foi alterado para "${res.status}"`;
            this.msgTipo = "verde"
            setTimeout(() => this.msg = "",3000);
            // recarrega lista
            this.getPedidos();
        }
    },
    mounted() {
        this.getPedidos();
        this.getStatus();
    }
}
</script>
<style scoped>
#burguer-table {
max-width: 400px;
margin: 0 auto;
}
#burguer-table-heading,
#burguer-table-rows,
.burguer-table-row {
display: flex;
flex-wrap: wrap;
}
#burguer-table-heading {
    font-weight: bold;
    padding: 12px;
    border-bottom: 3px solid #333;
}
#burguer-table-heading div,
.burguer-table-row div {
    width: 18%;
}
.burguer-table-row  {
    width: 100%;
    padding: 12px;
    border-bottom: 1px solid #ccc;
}

#burguer-table-heading .acoes,
#burguer-table-rows .acoes {
    width: 21%;

}
#burguer-table-heading .order-id,
#burguer-table-rows .order-id {
    width: 5%;

}
select {
    padding: 10px 6px;
    margin-right: 10px;
    font-size: 14px;
}
.status {

}
.delete-btn {
background-color: #222;
color:#FCBA03;
font-weight: bold;
border: 2px solid #222;
padding: 10px;
font-size: 14px;
margin: 0 auto;
cursor: pointer;
transition: .5s;
}
.delete-btn:hover {
    background-color: transparent;
    color: #222;
}
</style>