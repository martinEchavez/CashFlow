<script setup lang="ts">
import { computed } from 'vue';

const props = defineProps<{
    label: string,
    date?: Date,
    amount?: number,
    totalAmount: number
}>();

const currencyFormater = new Intl.NumberFormat(("es-CO"), {
  style: "currency", currency: "COP"
})

const amountVisual = computed(() => props.amount ? props.amount : props.totalAmount);
const amountCurrency = computed(() => currencyFormater.format(amountVisual.value));
const labelVisual = computed(() => props.date ? props.date.toDateString() : props.label);

</script>

<template>
    <main>
        <p>{{ labelVisual }}</p>
        <h1>{{ amountCurrency }}</h1>
        <div class="graphic">
          <slot name="graphic"></slot>
        </div>
        <div class="action">
          <slot name="action"></slot>
        </div>
    </main>
</template>

<style scoped>
main {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  width: 100%;
}
h1,
p {
  margin: 0;
  text-align: center;
}
h1 {
  margin-top: 14px;
  color: var(--brand-green);
}
.graphic {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  padding: 48px 24px;
  box-sizing: border-box;
}
</style>