<template>
  <div v-bind:class="[{ successfulClass: alertType === 'successful', unsuccessfulClass: alertType === 'unsuccessful',   confirmationClass: alertType === 'confirmation' }, 'alert__box']">
      <div v-bind:class="[{ successfulClassIcon: alertType === 'successful', unsuccessfulClassIcon: alertType === 'unsuccessful',   confirmationClassIcon: alertType === 'confirmation' }, 'icon']"></div>
      <div class="message">{{ message }}</div>
  </div>
</template>

<script>
  export default {
    name: 'Alert',
    props: {
      alertType: String,
      message: String
    }
  };
</script>

<style>
  .alert__box{
    display: flex;
    width: 60%;
    margin: 30px auto;
    padding: 30px;
    border-radius: 5px;
  }
  .successfulClass{
    background-color: #E9FFEE;
    border-left: 5px solid #44B86A;
    color: #408859;
  }
  .confirmationClass{
    background-color: #E5E9F6;
    border-left: 5px solid #60558D;
    color: #160361;
  }
  .unsuccessfulClass{
    background-color: #FFE9E9;
    border-left: 5px solid #EE1B28;
    color: #CF0D15;
  }
  .icon{
    width: 50px;
    height: 50px;
  }
  .successfulClassIcon{
    background-image: url("../assets/img/success.png");
    background-size: cover;
  }
  .confirmationClassIcon{
    background-color: white;
    border-radius: 50px;
  }
  .unsuccessfulClassIcon{
    background-image: url("../assets/img/failed.png");
    background-size: cover;
  }
  .message{
    margin-left: 30px;
    display: flex;
    align-items: center;
  }
</style>
