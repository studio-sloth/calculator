<template>
  <div class="calculator">
    <div class="screen">{{ current || 0 }}</div>
    <div class="row">
      <input type="button" v-on:click="operationSelect" class="btn-7" value="7"/>
      <input type="button" v-on:click="operationSelect" class="btn-8" value="8"/>
      <input type="button" v-on:click="operationSelect" class="btn-9" value="9"/>
      <input type="button" v-on:click="operationSelect" class="btn-equals" value="="/>
    </div>
    <div class="row">
      <input type="button" v-on:click="operationSelect" class="btn-4" value="4"/>
      <input type="button" v-on:click="operationSelect" class="btn-5" value="5"/>
      <input type="button" v-on:click="operationSelect" class="btn-6" value="6"/>
      <input type="button" v-on:click="operationSelect" class="btn-clear" value="C"/>
    </div>
    <div class="row">
      <input type="button" v-on:click="operationSelect" class="btn-1" value="1"/>
      <input type="button" v-on:click="operationSelect" class="btn-2" value="2"/>
      <input type="button" v-on:click="operationSelect" class="btn-3" value="3"/>
      <input type="button" v-on:click="operationSelect" class="btn-clear-all" value="AC"/>
    </div>
    <div class="row">
      <input type="button" v-on:click="operationSelect" class="btn-invert" value="+/-"/>
      <input type="button" v-on:click="operationSelect" class="btn-0" value="0"/>
      <input type="button" v-on:click="operationSelect" class="btn-decimal" value=","/>
      <input type="button" v-on:click="operationSelect" class="btn-modulus" value="%"/>
    </div>
    <div class="row">
      <input type="button" v-on:click="operationSelect" class="btn-add" value="+"/>
      <input type="button" v-on:click="operationSelect" class="btn-subtract" value="-"/>
      <input type="button" v-on:click="operationSelect" class="btn-multiply" value="*"/>
      <input type="button" v-on:click="operationSelect" class="btn-divide" value="/"/>
    </div>
    <!-- <pre>{{ memo }}</pre> -->
  </div>
</template>

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
