<template>
    <main id="order">

        <div class="order-form-wrapper container">

            <form @submit="postOrder" class="form">

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

                <div class="form-column">
                    <label for="products"><span>4</span><i class="fas fa-angle-double-right"></i>Podaj kod produktu</label>

                    <div class="form-row" v-for="(product, index) in orders.products" :key="index">
                        <input type="text" v-model="product.productName" placeholder="Wpisz nazwę produktu">
                        <input type="text" v-model="product.productId" placeholder="Wpisz kod produktu">
                        <input type="text" v-model="product.productQuantity" placeholder="Wpisz ilość">
                    </div>

                    <button @click.prevent:="addProductRow">Dodaj produkt</button>
                </div>
                
                <button type="submit" class="btn-order">Wyślij zamówienie</button>
            </form>

        </div>

    </main>
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

      let proxy = 'https://cors-anywhere.herokuapp.com/'

      axios.post('https://dakotha-faberlic-app.firebaseio.com/order', this.orders)
        .then((res) => {
          console.log('Zamówienie zapisane w bazie danych.')
        }).catch((error) => {
          console.log(error)
        })
    }
  }
}
</script>

<style lang="scss">
#order {
    background-color: rgba(0, 0, 0, .03);
}

.order-form-wrapper {
    background-color: transparent;
}

.form {
    // display: flex;
    // flex-direction: column;
    // align-items: center;

    input {
        margin-left: 5rem;
        padding: 1rem 0;
        font-family: 'Montserrat', sans-serif;
        font-size: 3rem;
        color: #666666;
        background-color: transparent;
        border: none;
        border-bottom: 1px solid #cccccc;
        outline: none;

        &::placeholder {
            color: #cccccc;
        }

        &:focus {
            border: none !important;
        }
    }

    .form-column {
        display: flex;
        flex-direction: column;
        padding-top: 10rem;
        
        label {
            margin: 1rem 0;
            font-family: 'Montserrat', sans-serif;
            font-size: 2.5rem;
            font-weight: 700;
            color: #666666;

            span {
                font-weight: 400;
            }

            i {
                margin: 0 1rem;
                font-size: 1.6rem;
            }
        }
    }

    button {
        margin: 5rem auto;
        // padding: 1rem 2rem;
    }
}

.form-row {
    display: flex;
    justify-content: flex-start;

    input {
        // margin-left: 5rem;
        font-size: 2rem;
        // border: none;
        // border-bottom: 1px solid lightgrey;
        // outline: none;
    }
}
</style>

