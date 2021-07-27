<template>
    <div>
        <h1>Incrementer</h1>
        <button @click="incrementCounter()" class="btn btn-primary">Increment</button>
        <button @click="decrementCounter()" class="btn btn-primary">Decrement</button>
        <div class="count">
            Count: <h3>{{count}}</h3>
        </div>
    </div>
</template>

<script lang="ts">
import { defineComponent, computed } from 'vue';
import { useStore } from 'vuex';

export default defineComponent({
    name: 'Incrementer',
    setup() {
        const store = useStore();
        
        return {
            count: computed(() => store.state.count),
            incrementCounter: () => store.commit('increment'),
            decrementCounter: () => store.commit('decrement')
        }
    }
})
</script>

<style scoped>
.count {
    display: block;
    margin: 5px;
}

.btn {
    margin: 5px;
}
</style>