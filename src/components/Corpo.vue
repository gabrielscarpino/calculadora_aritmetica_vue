<script setup>
const props = defineProps({
    calcularResultado: [String, Number], // resultado calculado
    estado: Object
})
</script>

<template>

    <div class="bg-light">
        <div class="row  mb-3 p-5">
            <div class="col-md-12">

                <input class="form-control text-center harmonizar_caixas" type="number" :value="props.estado.num1"
                    @input="evento => props.estado.num1 = Number(evento.target.value)"
                    placeholder="Digite o primeiro número">
            </div>




            <div class="col-md-12">
                <select class="form-select text-center box mt-5 mb-5 harmonizar_caixas" :value="props.estado.operacao"
                    @change="evento => props.estado.operacao = evento.target.value">


                    <option value="" disabled selected hidden>Selecione uma operação</option>
                    <option value="somar">Somar </option>
                    <option value="subtrair">Subtrair</option>
                    <option value="dividir">Dividir</option>
                    <option value="multiplicar">Multiplicar</option>
                </select>
            </div>


            <div class="col-md-12">
                <input class="form-control text-center harmonizar_caixas" type="number" :value="props.estado.num2"
                    @input="evento => props.estado.num2 = Number(evento.target.value)"
                    placeholder="Digite o segundo número">
            </div>
        </div>





        <div class="row ">
            <div class="col-md-12 text-center  mb-5 bg-primary text-white resultado p-3  rounded-5">
                <h4 class="fs-3"> Resultado: {{ props.calcularResultado }}</h4>
            </div>
        </div>
    </div>

</template>


<style scoped>
.resultado {
    margin: 0 auto;
    width: 100%;
    max-width: 320px;
    white-space: normal;
    word-break: break-word;
    display: inline-block;
}

.harmonizar_caixas {
    max-width: 640px;
    margin: 0 auto;
}
</style>