<template>
  <div v-bind:class="[{ successfulClass: alertType === 'successful', unsuccessfulClass: alertType === 'unsuccessful',   confirmationClass: alertType === 'confirmation' }, 'alert__box']">
      <div v-bind:class="[{ successfulClassIcon: alertType === 'successful', unsuccessfulClassIcon: alertType === 'unsuccessful',   confirmationClassIcon: alertType === 'confirmation' }, 'icon']"><div class="countdown" v-if="alertType === 'confirmation'">{{ countDown }}</div> </div>
      <div class="message">{{ message }}
        <div class="submessage__confirmation" v-if="alertType === 'confirmation'"><a href="#">Odeslat SMS</a> s povrzovacím kódem.</div>
      </div><div class="submessage__unsuccessful" v-if="alertType === 'unsuccessful'"><div class="icon__refresh"></div><a href="#"> Zkusit znovu</a></div>
  </div>
</template>

<script>
  export default {
    name: 'Alert',
    data() {
      return {
        countDown : 10
      }
    },
    props: {
      alertType: String,
      message: String
    },
    methods: {
      countDownTimer() {
        if(this.countDown > 0) {
          setTimeout(() => {
            this.countDown -= 1
            this.countDownTimer()
          }, 1000)
        }
      }
    },
    created() {
      this.countDownTimer()
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
  .alert__box a{
    color: #60558D;
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
    border: 8px solid #CACFDC;
  }
  .unsuccessfulClassIcon{
    background-image: url("../assets/img/failed.png");
    background-size: cover;
  }
  .message{
    margin-left: 30px;
    display: flex;
    flex-direction: column;
    align-self: center;
    font-weight: 700;
  }
  .submessage__confirmation{
     font-weight: 400;
     margin-top: 16px;
  }
  .submessage__unsuccessful{
    font-weight: 400;
    align-self: center;
    margin-left: 30px;
    display: flex;
    flex-direction: row;
  }
  .icon__refresh{
    background-image: url("../assets/img/refresh.png");
    background-size: cover;
    width: 22px;
    height: 22px;
    margin-right: 8px;
  }
  .countdown{
    text-align: center;
    margin-top: 5px;
  }

</style>
