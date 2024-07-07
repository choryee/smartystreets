<template>
  <div class="autocomplete">

    <InputForm :data="this"/>

    <span>위는 InputForm.vue
      <br/>
      바로 밑에 찍히는 것 :  Autocomplete.vue</span>
    <div v-for="suggestion in suggestions">
      <div class="autocomplete--suggestion"
           v-on:click="() => selectSuggestion(suggestion)">

        {{ formatSuggestion(suggestion, this.country.iso2).address }}
      </div>
    </div>

    <div v-if="error">
      <h3>Error:</h3>
      {{ error }}
    </div>
  </div>
</template>

<script>
//        v-on:click="() => selectSuggestion(suggestion)">
// 위 11라인은 원래 코드에서 위였음.

import InputForm from "./InputForm";

import {
  queryAutocompleteForSuggestions,
  selectSuggestion,
  validateAddress,
  updateStateFromValidatedAddress,
  formatSuggestion
} from "../../utils.js";

export default {
  name: "Autocomplete",
  components: {InputForm},

  data() {
    return {
      shouldValidate: true,
      address1: "",
      address2: "",
      city: "",
      state: "",
      zipCode: "",
      country: "US",
      suggestions: [],
      error: "",
    };
  },

  methods: {
    queryAutocompleteForSuggestions,
    selectSuggestion,
    validateAddress,
    updateStateFromValidatedAddress,
    formatSuggestion,
  },
};
</script>

<style scoped>
  .autocomplete {
    max-width: 800px;
    margin-left: auto;
    margin-right: auto;
  }

  .autocomplete--suggestion {
    font-family: Helvetica, Arial, sans-serif;
    padding: 5px 10px;
  }

  .autocomplete--suggestion:hover {
      background-color: #D9ECF0;
      color: #02355A;
      cursor: pointer;
  }
</style>
