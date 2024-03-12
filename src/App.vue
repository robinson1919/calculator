<template>
  <div class="container">
    <div class="calculator">
      <form action="">
        <div class="display">
          <input type="text" name="display" v-model="display">
        </div>
        <div>
          <input type="button" value="AC" @click="actions" class="operator">
          <input type="button" value="DE" @click="actions" class="operator">
          <input type="button" value="." @click="actions" class="operator">
          <input type="button" value="/" @click="actions" class="operator">
        </div>
        <div>
          <input type="button" value="7" @click="actions">
          <input type="button" value="8" @click="actions">
          <input type="button" value="9" @click="actions">
          <input type="button" value="*" @click="actions" class="operator">
        </div>
        <div>
          <input type="button" value="4" @click="actions">
          <input type="button" value="5" @click="actions">
          <input type="button" value="6" @click="actions">
          <input type="button" value="-" @click="actions" class="operator">
        </div>
        <div>
          <input type="button" value="1" @click="actions">
          <input type="button" value="2" @click="actions">
          <input type="button" value="3" @click="actions">
          <input type="button" value="+" @click="actions" class="operator">
        </div>
        <div>
          <input type="button" value="00" @click="actions">
          <input type="button" value="0" @click="actions">
          <input type="button" value="=" @click="actions" class="equal operator">
        </div>
      </form>
    </div>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data: () => ({
    display: '',
  }),
  methods: {
    actions({target: {value}}){

      if(value == 'AC') this.display = '';
      if(value == 'DE') this.display = this.display.toString().slice(0, -1);
      if(value == '=') this.display = eval(this.display); 

      if (this.display.length >= 12 || value == 'AC' || value == 'DE' || value == '=') return
      this.display += value      
    }
  },
}
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.container {
  width: 100%;
  height: 100vh;
  background: #e3f9ff;
  display: flex;
  align-items: center;
  justify-content: center;
}

.calculator {
  background: #3a4452;
  padding: 30px;
  border-radius: 10px;
}

.calculator form input {
  border: 0;
  outline: 0;
  width: 60px;
  height: 60px;
  border-radius: 10px;
  box-shadow: -8px -8px 10px rgba(255, 255, 255, 0.1), 5px 5px 15px rgba(0, 0, 0, 0.2);
  background: transparent;
  font-size: 20px;
  color: #fff;
  cursor: pointer;
  margin: 10px;
}

form .display {
  display: flex;
  justify-content: flex-end;
  margin: 20px 0;
}

form .display input {
  text-align: right;
  flex: 1;
  font-size: 45px;
  box-shadow: none;
}

form input.equal {
  width: 145px;
}

form input.operator {
  color: #33ffd8;
}
</style>
