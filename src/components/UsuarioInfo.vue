<template>
    <div class="componente">
        <h2>As Informações de Usuário</h2>
        <p>Vários detalhes...</p>
        <p>Nome do Usuário: <strong> {{ inverterLetras() }}</strong></p>
        <p>Idade do usuário: <strong>{{ idade }}</strong></p>
        <button @click="reiniciarNome">Reiniciar Nome</button>
        <button @click="reinciarFn">Reiniciar Nome (CallBack)</button>
    </div>
</template>

<script>
export default {
    props: {
        nome: {
            type: String,
            //required: true
            default: 'Anônimo'
            /* default: function() {
                return Array(10).fill(23).join(',')
            } */
        },
        reinciarFn: Function,
        idade: Number
    },
    methods: {
        inverterLetras() {
            return this.nome.split('').reverse().join('')
        },
        reiniciarNome() {
            /* eslint-disable */
            const antigo = this.nome
            
            this.nome = 'Leandro'
            //Evento para informar o pai que houve alteração
            this.$emit('AlteradoPeloFilho', this.nome)
            /* {
                novo: this.nome,
                antigo
            }) */
        }
    }
}
</script>

<style scoped>
    .componente {
        flex: 1;
        background-color: #ec485f;
        color: #fff;
    }
</style>
