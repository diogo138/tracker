<template>
    <div class="box">
        <div class="columns">
            <div class="column is-8" role="form" aria-label="formulario para criação de uma nova tarefa">
                <input type="text" v-model="descricao" class="input" name="" id="" placeholder="Qual Tarefa você deseja iniciar?">
            </div>
            <div class="column">
                <Temporizador @aoTemporizadorFinalizado="finalizarTarefa"/>
            </div>
        </div>
    </div>
</template>
<script lang="ts">
    import { defineComponent } from 'vue';
    import Temporizador from './Temporizador.vue'

    export default defineComponent({
        name: 'Formulario',
        emits: ['aoSalvarTarefa'],
        components: {
            Temporizador
        },
        data() {
            return {
                descricao: ''
            }
        },
        methods: {
            finalizarTarefa(tempoDecorrido: number): void {
                this.$emit('aoSalvarTarefa', {
                    descricao: this.descricao,
                    duracaoEmSegundos: tempoDecorrido
                });
                this.descricao = '';
            }
        }
    });
</script>

<style scoped>

</style>
