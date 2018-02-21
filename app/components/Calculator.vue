<template>
  <div class="calculator">
    <div class="screen">{{ current || 0 }}</div>
    <div class="row">
      <input type="button" v-on:click="operationSelect" class="btn btn-7" value="7"/>
      <input type="button" v-on:click="operationSelect" class="btn btn-8" value="8"/>
      <input type="button" v-on:click="operationSelect" class="btn btn-9" value="9"/>
      <input type="button" v-on:click="operationSelect" class="btn btn-equals" value="="/>
    </div>
    <div class="row">
      <input type="button" v-on:click="operationSelect" class="btn btn-4" value="4"/>
      <input type="button" v-on:click="operationSelect" class="btn btn-5" value="5"/>
      <input type="button" v-on:click="operationSelect" class="btn btn-6" value="6"/>
      <input type="button" v-on:click="operationSelect" class="btn btn-clear" value="C"/>
    </div>
    <div class="row">
      <input type="button" v-on:click="operationSelect" class="btn btn-1" value="1"/>
      <input type="button" v-on:click="operationSelect" class="btn btn-2" value="2"/>
      <input type="button" v-on:click="operationSelect" class="btn btn-3" value="3"/>
      <input type="button" v-on:click="operationSelect" class="btn btn-clear-all" value="AC"/>
    </div>
    <div class="row">
      <input type="button" v-on:click="operationSelect" class="btn btn-invert" value="+/-"/>
      <input type="button" v-on:click="operationSelect" class="btn btn-0" value="0"/>
      <input type="button" v-on:click="operationSelect" class="btn btn-decimal" value=","/>
      <input type="button" v-on:click="operationSelect" class="btn btn-modulus" value="%"/>
    </div>
    <div class="row">
      <input type="button" v-on:click="operationSelect" class="btn btn-add" value="+"/>
      <input type="button" v-on:click="operationSelect" class="btn btn-subtract" value="-"/>
      <input type="button" v-on:click="operationSelect" class="btn btn-multiply" value="*"/>
      <input type="button" v-on:click="operationSelect" class="btn btn-divide" value="/"/>
    </div>
    <!-- <pre>{{ memo }}</pre> -->
  </div>
</template>

<style scoped>
  .calculator {
    background: #F3F564;
    box-shadow: 0 6px 10px 0 rgba(0,0,0,0.50), inset 0 1px 18px 0 #7A7B1C;
    border-radius: 18.18px;
    width: 285px;
    height: 400px;
    margin: 0 auto;
    padding: 35px;
    display: flex;
    align-items: stretch;
    justify-content: space-between;
    flex-direction: column;
  }
  .calculator .screen {
    background: #E8E8E8;
    box-shadow: inset 0 1px 10px 0 rgba(0,0,0,0.50);
    border-radius: 14px;
    min-height: 60px;
    display: flex;
    align-items: center;
    justify-content: flex-end;
    padding: 20px;
  }
  .calculator .row {
    display: flex;
    align-items: stretch;
    justify-content: space-between;
    background: #525050;
    box-shadow: 0 2px 4px 0 rgba(0,0,0,0.50), inset 0 1px 22px 0 rgba(0,0,0,0.50);
    border-radius: 15px;
  }
  .btn {
    font-size: 20px;
    color: #D7F847;
    letter-spacing: 7.42px;
    flex: 1 0 25%;
    height: 100%;
    background: transparent;
    border: none;
    box-shadow: none;
    height: 100%;
  }
  .btn:focus {
    outline: none;
  }
</style>

<script>
  export default {
    name: 'calculator',
    data() {
      return {
        current: '',
        memo: '',
      }
    },

    methods: {

      operationSelect: function(event) {

        let value = event.target.value;

        // what is our operation?
        switch (value) {

          case '+':
          case '-':
          case 'x':
          case '÷':
            this.memo += `${value}`;
            this.current += `${value}`;
            break;

          // equals
          case '=':
            this.current = eval(this.memo);
            this.memo = this.current;
            break;

          // clear
          case 'C':
          case 'AC':
            this.current = '';
            this.memo = '';
            break;

          case '+/-':
            let val = eval(this.memo);
            this.memo = `${val * -1}`;
            this.current = `${this.memo}`;
            break;

          default:
            this.current += `${value}`;
            this.memo += `${value}`;
            break;

        }

      }
    }
  }

</script>
