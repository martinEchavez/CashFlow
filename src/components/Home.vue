<script setup lang="ts">
import Layout from './Layout.vue';
import Header from './Header.vue';
import Resume from './Resume/index.vue'
import Movements from './Movements.vue';
import { ref, type Ref } from 'vue';

const amount: Ref<number | undefined> = ref();
const date: Ref<Date | undefined> = ref( new Date(2024, 2, 11));

</script>

<template>
    <Layout>
        <template #header>
            <Header></Header>
        </template>
        <template #resume>
            <Resume
                :label="'Ahorro total'"
                :date="date"
                :amount=amount
                :total-amount="2000000"
            />
        </template>
        <template #movements>
            <Movements />
        </template>
    </Layout>
</template>