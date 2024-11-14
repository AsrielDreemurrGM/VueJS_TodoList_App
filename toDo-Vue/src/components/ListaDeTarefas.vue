<script setup>
const props = defineProps(['tarefas','tarefasPendentes']);
</script>

<template>
    <ul class="list-group mt-4">
        <li v-if="props.tarefasPendentes > 0" class="list-group-item" v-for="tarefa in props.tarefas">
            <input @change="evento => tarefa.finalizada = evento.target.checked" :checked="tarefa.finalizada"
                :id="tarefa.titulo" type="checkbox">
            <label :class="{ finished: tarefa.finalizada }" class="ms-3" :for="tarefa.titulo">
                {{ tarefa.titulo }}
            </label>
        </li>
        <li class="list-unstyled" v-else="">Não existem tarefas pendentes. Adicione uma nova tarefa.</li>
    </ul>
</template>

<style scoped>
.finished {
    text-decoration: line-through;
}
</style>
