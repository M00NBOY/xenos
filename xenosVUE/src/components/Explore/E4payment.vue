<template>
  <div class="payment">
    <div class="one">
      <h5 class="title">1. Select you payment method</h5>
      <div class="methods">
        <div class="cb" @click="oneOk">
          <img src="@/assets/img/payment-cb.png" alt="">
          <p>CB</p>
        </div>
        <div class="mt" @click="oneOk">
          <img src="@/assets/img/payment-maestro.png" alt="">
          <p>Maestro</p>
        </div>
        <div class="mc" @click="oneOk">
          <img src="@/assets/img/payment-mastercard.png" alt="">
          <p>Mastercard</p>
        </div>
        <div class="v" @click="oneOk">
          <img src="@/assets/img/payment-visa.png" alt="">
          <p>Visa</p>
        </div>
      </div>
    </div>

    <div class="two" :class="{active: one}">
      <h5 class="title">2. Card details</h5>
      <label class="card">Card n°</label>
      <input type="text" class="card" placeholder="1234  5678 9012 3456">
      <label class="expire">Expiry date</label>
      <input type="text" class="expire" placeholder="10/02">
      <label class="cvv">Cvv</label>
      <input type="text" class="cvv" placeholder="123">
    </div>

    <transition name="slide-right">
      <router-link :to="`/explore/${$route.params.planet}/${zone.name}/done`">
        <button
          @click="$emit('nextStep')"
          
        >Confirm</button>
      </router-link>
    </transition>
  </div>
</template>

<script>
export default {
  name: 'E4payment',
  props: ['planet', 'zone'],
  data: function () {
    return {
      one: false
    }
  },
  methods: {
    oneOk: function () {
      this.one = true
    },
  }
}
</script>


<style lang="scss" scoped>
.payment {
  color: var(--main-dark-white);
  padding-bottom: 80px;
  .one {
    margin-top: 40px;
    .methods {
      margin-top: 20px;
      display: flex;
      align-items: flex-end;
      > div {
        display: flex;
        flex-direction: column;
        align-items: center;
        margin-right: 20px;
        > p {
          margin-top: 6px;
        }
      }
      .v img {
        margin-bottom: 6px;
      }
    }
  }
  .two {
    margin-top: 40px;
    display: flex;
    flex-direction: column;
    opacity: .3;
    .title {
      margin-bottom: 10px;
    }
    label {
    }
    input {
      padding: 10px 8px;
      border-radius: 4px;
      border: none;
      margin-top: 8px;
      background-color: var(--secondary-dark);
      margin-bottom: 20px;
      box-sizing: border-box;
      color: var(--main-white);
      outline: none;
    }
  }
  .active {
    opacity: 1;
  }
}
</style>

