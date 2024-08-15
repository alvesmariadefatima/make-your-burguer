<template>
    <div>
        <!-- Exibe a mensagem somente quando `msg` não é nulo ou vazio -->
        <Message v-if="msg" :msg="msg" />
        <div>
            <form id="burger-form" @submit.prevent="createBurguer">
                <div class="input-container">
                    <label for="nome">Nome do cliente: </label>
                    <input type="text" id="nome" v-model="nome" placeholder="Digite o seu nome">
                </div>

                <div class="input-container">
                    <label for="pao">Escolha o Pão: </label>
                    <select name="pao" id="pao" v-model="pao">
                        <option value="">Selecione o seu pão</option>
                        <option v-for="pao in paes" :key="pao.tipo" :value="pao.tipo">{{ pao.tipo }}</option>
                    </select>
                </div>

                <div class="input-container">
                    <label for="carne">Selecione o tipo de carne:</label>
                    <select name="carne" id="carne" v-model="carne">
                        <option value="">Selecione o tipo de carne</option>
                        <option v-for="carne in carnes" :key="carne.id" :value="carne.tipo">{{ carne.tipo }}</option>
                    </select>
                </div>

                <div id="opcionais-container" class="input-container">
                    <label id="opcionais-title" for="opcionais">Selecione os opcionais: </label>
                    <div class="checkbox-container" v-for="opcional in opcionaisData" :key="opcional.id">
                        <input type="checkbox" v-model="opcionais" class="opcionais" :value="opcional.tipo">
                        <span>{{ opcional.tipo }}</span>
                    </div>
                </div>

                <div class="input-container">
                    <input type="submit" class="submit-btn" value="Criar meu Burger!">
                </div>
            </form>
        </div>
    </div>
</template>

<script>
import Message from './Message.vue';

export default {
    name: "BurgerForm",
    components: {
        Message
    },
    data() {
        return {
            paes: [],
            carnes: [],
            opcionaisData: [],
            nome: "",
            pao: "",
            carne: "",
            opcionais: [],
            msg: ""  // Mensagem de sucesso ou erro
        }
    },
    methods: {
        async getIngredientes() {
            try {
                const req = await fetch('http://localhost:3000/ingredientes');
                const data = await req.json();
                this.paes = data.paes;
                this.carnes = data.carnes;
                this.opcionaisData = data.opcionais;
            } catch (error) {
                console.error('Erro ao buscar ingredientes:', error);
            }
        },
        async createBurguer() {
            try {
                const data = {
                    nome: this.nome,
                    carne: this.carne,
                    pao: this.pao,
                    opcionais: this.opcionais,
                    status: "Solicitado",
                };

                const dataJson = JSON.stringify(data);
                const req = await fetch("http://localhost:3000/burgers", {
                    method: "POST",
                    headers: { "Content-Type": "application/json" },
                    body: dataJson
                });
                const res = await req.json();

                // Mostrar mensagem de sucesso
                this.msg = `Pedido Nº ${res.id} realizado com sucesso!`;

                // Limpar mensagem após 3 segundos
                setTimeout(() => this.msg = "", 3000);

                // Limpar os campos
                this.nome = "";
                this.carne = "";
                this.pao = "";
                this.opcionais = [];
            } catch (error) {
                console.error('Erro ao criar o burger:', error);
                this.msg = "Ocorreu um erro ao criar o burger.";
            }
        }
    },
    mounted() {
        this.getIngredientes();
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
        border-left: 4px solid #FCBA03;
    }

    input, select {
        padding: 5px 10px;
        width: 300px;
    }

    #opcionais-container {
        display: flex;
        flex-wrap: wrap;
    }

    #opcionais-title {
        width: 100%;
    }

    .checkbox-container {
        width: calc(33.33% - 10px);
        display: flex;
        align-items: center;
        margin-bottom: 20px;
        margin-right: 10px;
    }

    .checkbox-container:last-child {
        margin-right: 0; /* Remove o espaço direito do último item */
    }

    .checkbox-container span,
    .checkbox-container input {
        width: auto;
    }

    .checkbox-container span {
        margin-left: 6px;
        font-weight: bold;
    }

    .submit-btn {
        background-color: #222;
        color: #FCBA03;
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