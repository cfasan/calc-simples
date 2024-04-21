<script setup>
    const props = defineProps(['primeiroValor', 'valorUm', 'operacao', 'segundoValor', 'valorDois', 'calcular', 'resultado']);
</script>

<template>
    <main>
        <div class="main_header">
        <h2>Calculadora Simples</h2>
    </div>
    <div class="main_body">
        <form>
            <div>
                <input type="text" placeholder="Valor 1" v-model="props.primeiroValor" @keyup="props.valorUm" />
            <select @change="props.calcular" v-model="props.operacao">
                <option value="adicao" selected>+</option>
                <option value="subtracao">-</option>
                <option value="multiplicacao">*</option>
                <option value="divisao">/</option>
                <option value="potenciacao">^</option>
            </select>
            <input type="text" placeholder="Valor 2" v-model="props.segundoValor" @keyup="props.valorDois" />
            </div>
            <button type="reset">Limpar</button>
        </form>
    </div>
    <div class="main_footer">
        <span class="titulo_resultado">Resultado</span>
        <span class="valor_resultado">{{ props.resultado }}</span>
    </div>
    </main>
</template>