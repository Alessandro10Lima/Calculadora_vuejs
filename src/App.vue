<script setup>
import { reactive } from 'vue';
const estado = reactive({
    filtro: 'soma',
    num1:0,
    num2:0,
});

const getSoma = () => {
    return Number(estado.num1) + Number(estado.num2);
}
const getDiminui = () => {
    return estado.num1 - estado.num2;
}
const getMultiplica = () => {
    return estado.num1 * estado.num2;
}
const getDivide = () => {
    return estado.num1 / estado.num2;
}

const getOperaçoes = () => {
    const {filtro} = estado;

    switch(filtro){
        case 'soma':
            return getSoma();
        case 'subtracao':
            return getDiminui();
        case 'multiplicacao':
            return getMultiplica();
        case 'divisao':
            return getDivide();
        default:
            return null;
    }
};
</script>

<template>
<div class="container bg-light">
    <header class="p-5 mt-4 mb-4 rounded-3 bg-primary">
    <h1 class="text-white">Calculadora</h1>
</header>
    <form>
        <div class="row">
            <div class="col mb-3">
                <label for="">Primeiro número:</label>
                <input @keyup="evento => estado.num1 = evento.target.value" type="number" class="form-control">
            </div>
        </div>
        <div class="col">
            <label for="">Segundo número:</label>
            <input @keyup="evento => estado.num2 = evento.target.value" type="number" class="form-control">
        </div>
        <div class="col-md-2">
            <select @change="evento => estado.filtro = evento.target.value" class="form-control mt-3 mb-3">
                <option value="soma">Somar</option>
                <option value="subtracao">Subtrair</option>
                <option value="multiplicacao">Multiplicar</option>
                <option value="divisao">Dividir</option>
            </select>
        </div>
        <span class="fw-bold" v-if="estado.num1 && estado.num2">Resultado = {{ getOperaçoes() }}</span>
    </form>
</div>
</template>

<style scoped>
.form-control{
    cursor: pointer;
}

</style>
