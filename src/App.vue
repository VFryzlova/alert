<template>
  <div>
    <Alert v-bind:alertType="'successful'" v-bind:message="successMessage" />
    <Alert v-bind:alertType="'confirmation'" v-bind:message="confirmationMessage" />
    <Alert v-bind:alertType="'unsuccessful'" v-bind:message="failedMessage" />
  </div>
</template>

<script>
  import Alert from "./components/Alert.vue";
  export default {
    name: 'App',
    components: {
      Alert: Alert
    },
    data(){
      return{
        successMessage: "Požadavek byl potvrzen.",
        confirmationMessage: "Potvrzení požadavku.",
        failedMessage: "Požadavek nebyl potvrzen."
      }
    }
  };
</script>

<style>
  *{
    box-sizing: border-box;
  }
  body{
    font-family: 'Roboto', sans-serif;
    margin: 0;
    padding: 0;
    background-color: #E5E5E5;
  }
</style>
