<template>
  <v-select
    class="country-code"
    :items="countryCodes"
    item-text="code"
    item-value="dial_code"
    color="#f36c21"
    outlined
    dark
    dense
    v-bind="$attrs"
    v-on="$listeners"
  >
    <template v-slot:item="data">
      {{ data.item.code }} - {{ data.item.name }} ({{
        '+' + data.item.dial_code
      }})
    </template>
  </v-select>
</template>

<script>
import CountryCodesJson from '@/assets/country-codes.json'

export default {
  data() {
    return {
      countryCodes: CountryCodesJson,
    }
  },
}
</script>

<style lang="scss" scoped>
.country-code {
  width: 80px !important;
  height: 40px !important;

  .v-text-field__details {
    display: none;
  }

  .v-input__control .v-input__slot {
    padding: 0 0 0 8px !important;
    margin: 0;
  }

  .v-select__slot .v-input__append-inner {
    color: red;
    padding: 0 !important;
  }
}
</style>