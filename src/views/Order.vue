<template>
  <div class="order container">
    <h1>Zamówienie</h1>

    <form @submit="postOrder">

      <div class="form-column">
        <label for="products"><span>4</span><i class="fas fa-angle-double-right"></i>Podaj kod produktu</label>

        <div class="form-row" v-for="(product, index) in orders.products" :key="index">
          <input type="text" v-model="product.productName" placeholder="Wpisz nazwę produktu">
          <input type="text" v-model="product.productId" placeholder="Wpisz kod produktu">
          <input type="text" v-model="product.productQuantity" placeholder="Wpisz ilość">
        </div>

        <button @click.prevent:="addProductRow">Dodaj produkt</button>
      </div>


      <div class="form-column">
        <label for="name"><span>1</span><i class="fas fa-angle-double-right"></i>Cześć, mam na imię Zenobia. Jak Ty się nazywasz?</label>
        <input type="text" id="name" v-model="orders.name" placeholder="Podaj swoje imię i nazwisko">
      </div>

      <div class="form-column">
        <label for="email"><span>2</span><i class="fas fa-angle-double-right"></i>Podaj proszę swój adres email.</label>
        <input type="text" id="email" v-model="orders.email" placeholder="Wpisz swój adres email">
      </div>

      <div class="form-column">
        <label for="address"><span>3</span><i class="fas fa-angle-double-right"></i>Podaj proszę adres do wysyłki Twojego zamówienia.</label>
        <input type="text" id="address" v-model="orders.address" placeholder="Wpisz adres do wysyłki zamówienia">
      </div>
     
      <button type="submit">Wyślij zamówienie</button>
    </form>


  </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'order',
  data: function () {
      return {
        orders: {
          name: '',
          email: '',
          address: '',
          products: [{}]
        }
      }
  },
  methods: {
    addProductRow(event) {
      event.preventDefault()

      this.orders.products.push({})
    },
    postOrder(event) {
      event.preventDefault()

      console.log(JSON.stringify(this.orders))
      axios.post('https://dakotha-faberlic-app.firebaseio.com/', this.orders)
    }
  }
}
</script>

<style lang="scss">
.container {
  margin: 0 auto;
  width: 1140px;
  // border: 1px solid red;
}

.form-row {
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
}

.form-row > input {
  margin-left: 5rem;
  font-size: 1rem;
  border: none;
  border-bottom: 1px solid lightgrey;
  outline: none;
}

.form-column {
  display: flex;
  flex-direction: column;
  margin: 5rem 0;
  font-size: 1rem;
  text-align: left;
}

.form-column > label {
  margin: 1rem 0;
}

.form-column > label > span {
  font-weight: 700;
}

.form-column > label > i {
  margin: 0 1rem;
}

.form-column > input {
  margin-left: 5rem;
  font-size: 1rem;
  border: none;
  border-bottom: 1px solid lightgrey;
  outline: none;
}
</style>

