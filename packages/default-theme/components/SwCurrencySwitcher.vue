<template>
  <!-- TODO: change this if after onMounted hook here is resolved -->
  <div
    v-if="activeCurrency && availableCurrencies.length > 1"
    class="sw-currency"
    data-cy="currency-switcher"
  >
    <SfSelect
      v-model="activeCurrency"
      :size="availableCurrencies.length"
      class="sw-currency__select sf-select--no-chevron"
      @click="loadAvailableCurrencies"
      data-cy="currency-switcher-select"
    >
      <SfSelectOption
        v-for="currencyItem in availableCurrencies"
        :key="currencyItem.id"
        :value="currencyItem.id"
        data-cy="currency-switcher-option"
      >
        {{ currencyItem.symbol }}
      </SfSelectOption>
    </SfSelect>
  </div>
</template>
<script>
import { SfSelect, SfProductOption } from "@storefront-ui/vue"
import { useCurrency } from "@shopware-pwa/composables"
import { computed, onMounted } from "@vue/composition-api"

export default {
  name: "SwCurrencySwitcher",
  components: {
    SfSelect,
  },
  setup(props, { root }) {
    const {
      currency,
      setCurrency,
      loadAvailableCurrencies,
      availableCurrencies,
    } = useCurrency(root)

    // TODO: loaded on mounted only untill fixed issue: https://github.com/DivanteLtd/storefront-ui/issues/1097
    onMounted(async () => {
      await loadAvailableCurrencies()
    })

    const activeCurrency = computed({
      get: () => currency.value && currency.value.id,
      set: async (id) => {
        await setCurrency({ id })
        root.$router.push({
          query: { ...root.$router.currentRoute.query, currencyId: id },
        })
      },
    })
    return {
      availableCurrencies,
      activeCurrency,
      loadAvailableCurrencies,
    }
  },
}
</script>
<style lang="scss" scoped>
@import "@/assets/scss/variables";

.sw-currency {
  --select-padding: 0;
  --select-margin: 0;
  --select-selected-padding: 0 var(--spacer-xs);
  --select-selected-justify-content: center;
  text-align: center;
  cursor: pointer;
}
</style>
