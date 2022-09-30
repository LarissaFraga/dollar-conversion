<template>
  <q-page class="flex items-center justify-center">
    <div class="container">
      <img
        style="margin-bottom: 15px"
        src="../../public/icons/attach_money_black_48dp.svg"
        alt="dollar symbol"
      />
      <q-input
        class="input"
        outlined
        v-model="real"
        prefix="R$"
        input-class="text-right"
        reverse-fill-mask
        style="margin-bottom: 1rem"
        :disable="showTotal"
      />
      <q-input
        class="input"
        outlined
        v-model="dollar"
        prefix="US$"
        input-class="text-right"
        reverse-fill-mask
        :disable="showTotal"
      />
      <div class="button-container">
        <q-btn
          color="white"
          text-color="primary"
          label="Clear"
          @click="clearFields()"
        />
        <q-btn
          color="primary"
          label="Calculate"
          @click="calculateConversion()"
        />
      </div>
      <p class="text" v-if="showTotal">
        With R${{ real }} it is possible to buy US${{ dollar }} at
        {{ total }} dollars each.
      </p>
    </div>
  </q-page>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'IndexPage',

  data() {
    return {
      real: 0,
      dollar: 0,
      total: 0,
      showTotal: false,
    }
  },
  methods: {
    clearFields() {
      this.real = 0
      this.dollar = 0
      this.showTotal = false
    },
    calculateConversion() {
      this.total = this.real / this.dollar
      this.total = parseFloat(this.total.toFixed(2))
      this.showTotal = true
    },
  },
})
</script>

<style lang="scss" scoped>
.input {
  margin-bottom: 1rem;
  width: 215px;
}

.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.button-container {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
  width: 215px;
}

.text {
  margin-top: 1rem;
  text-align: center;
}
</style>
