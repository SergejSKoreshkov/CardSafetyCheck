<template>
  <div class="card">
    <div class="card-offset" ref="offset">
      <h1 ref="h1">Don't let your money gone</h1>
      <h3 ref="h3">Check your card safety</h3>
      <form ref="form" method="get" action="/" @submit.prevent="send">
        <div class="card-body">
          <h4>Credit Card</h4>
          <p>Card number</p>
          <div class="code">
            <input type="number" required name="1" v-model="type" @keyup="setCardType"/>
            <input type="number" required name="2" />
            <input type="number" required name="3" />
            <input type="number" required name="4" />
          </div>
          <p>Month/Year</p>
          <div class="year-month">
            <div>
              <input type="number" required name="5" />
              <input type="number" required name="6" />
            </div>
            <img ref="cartTypeImage" src="https://upload.wikimedia.org/wikipedia/commons/5/5e/Visa_Inc._logo.svg"/>
          </div>
        </div>
        <div class="card-body">
          <div ref="line" class="inline">
            <div class="line"></div>
            <div class="line-ok"></div>
          </div>
          <p>CVC code</p>
          <div class="date">
            <input type="number" required  name="9" />
          </div>
        </div>
        <button type="submit">Check</button>
      </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Card',
  data () {
    return {
      type: 4000,
      cardTypes: {
        visa: "https://upload.wikimedia.org/wikipedia/commons/5/5e/Visa_Inc._logo.svg",
        masterCard: "https://upload.wikimedia.org/wikipedia/commons/2/2a/Mastercard-logo.svg",
        americanExpress: "https://upload.wikimedia.org/wikipedia/commons/f/fa/American_Express_logo_%282018%29.svg",
      }
    }
  },
  methods: {
    setCardType() {
      if (this.type.indexOf("51") === 0) {
        this.$refs.cartTypeImage.src = this.cardTypes.masterCard
      }
      if (this.type.indexOf("4") === 0) {
        this.$refs.cartTypeImage.src = this.cardTypes.visa
      }
      if (this.type.indexOf("34") === 0) {
        this.$refs.cartTypeImage.src = this.cardTypes.americanExpress
      }
    },
    send() {
      this.$refs.offset.classList.add('alert')
      setTimeout(() => {
        this.$refs.h3.innerHTML = "";
        this.$refs.h1.innerHTML = "Your card is safe!"
        this.$refs.line.classList.add('ok')
      }, 300)
    }
  }
}
</script>

<style scoped>
  .card {
    height: 100%;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  .card-offset {
    background: #ddd;
    box-shadow: inset 1em 1em 1em white;
    padding: 1em;
    border-radius: 10px;
    opacity: 0.9;
    max-width: 85vw;
    transition: .3s ease;
  }
  .card-body {
    margin: .5em;    
    position: relative;
    width: 400px;
    max-width: calc(100% - 1em);
    min-height: 200px;
    border-radius: 10px;
    background: #eee;
    transition: 1s ease;
    text-align: left;
    filter: saturate(1.5);
  }
  .card-body:hover {
    box-shadow: 0 0 15px #bbb;
  }
  .card-body h4 {
    padding: 1em;
    margin: 0;
  }
  .card-body p {
    padding: 0 0 0 1em;
    margin: 0;
    margin-bottom: 5px;
    margin-top: .5em;
  }
  button {
    padding: 1em 2em 1em 2em;
    background: #4CAF50 !important;
    color: white;
    font-weight: bold;
    border: none;
    border-radius: 10px;
    transition: .3s ease;
  }
  button:hover {
    background: #43A047 !important;
    outline: none;
    box-shadow: none;
  }
  button:active, button:focus {
    background: #43A047 !important;
    outline: none;
    box-shadow: none;
    transform: scale(0.9);
  }
  .code {
    display: flex;
    padding: 0 1em 0 1em;
    justify-content: space-between;
  }
  .date {
    display: flex;
    padding: 0 1em 0 1em;
    /* justify-content: space-between; */
  }
  .code input, .date input {
    width: 15%;
    border: none;
    background: #ddd;
    padding: .5em;
  }
  .date input {
    margin-right: 1em !important;
  }
  .line, .line-ok {
    background: #000;
    width: 100%;
    height: 35px;
    position: relative;
    top: 1em;
    margin-bottom: 2em;
    transition: .5s ease;
  }
  .line-ok {
    width: 0;
    transition: .5s ease;
    background: #4CAF50;
  }
  .ok .line {
    width: 0% !important;
  }
  .ok .line-ok {
    width: 100% !important;
  }
  .alert {
    animation: alertKeyframes 0.5s ease-in;
    transition-delay: 0.5s;
    background: #A5D6A7;
    box-shadow: none;
  }
  @keyframes alertKeyframes {
    0% {
      transform: translateX(0);
      background: #ddd;
      box-shadow: none;
    }
    100% {
      transform: translateX(0);
      box-shadow: none;
      background: #A5D6A7;
    }
  }
  .inline {
    display: flex;
  }
  .year-month {
    display: flex;
    justify-content: space-between;
    padding: 1em;
  }
  .year-month img {
    max-width: 20%;
    max-height: 45px;
  }
  .year-month input {
    width: 11%;
    margin-right: .5em;
    border: none;
    background: #ddd;
    padding: .5em;
  }
</style>
