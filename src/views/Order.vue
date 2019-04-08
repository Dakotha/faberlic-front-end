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
                    <label for="phone"><span>2</span><i class="fas fa-angle-double-right"></i>Podaj swój numer telefonu.</label>
                    <input type="text" id="phone" v-model="orders.phone" placeholder="Wpisz swój numer telefonu">
                </div>

                <div class="form-column">
                    <label for="address"><span>3</span><i class="fas fa-angle-double-right"></i>Podaj adres do wysyłki Twojego zamówienia.</label>
                    <input type="text" id="address" v-model="orders.address" placeholder="Wpisz adres do wysyłki zamówienia">
                </div>

                <div class="form-column">
                    <label for="products"><span>4</span><i class="fas fa-angle-double-right"></i>Podaj nazwy i kody produktów</label>

                    <div class="form-row" v-for="(product, index) in orders.products" :key="index">
                        <input type="text" v-model="product.productName" placeholder="Wpisz nazwę produktu">
                        <input type="text" v-model="product.productId" placeholder="Wpisz kod produktu">
                        <input type="text" v-model="product.productQuantity" placeholder="Wpisz ilość">
                        <button @click="removeProductRow(index)" class="remove-row"><i class="fas fa-trash-alt"></i></button>
                    </div>

                    <button @click="addProductRow" class="add-row">Dodaj produkt</button>
                </div>
                
                <button type="submit" class="btn-order">Wyślij zamówienie</button>
            </form>

        </div>

    </main>
</template>

<script>
import axios from 'axios'
import swal from 'sweetalert'

export default {
    name: 'order',
    data: function () {
        return {
            orders: {
                name: '',
                email: '',
                phone: '',
                address: '',
                products: [{}]
            }
        }
    },
    methods: {
        addProductRow() {
            this.orders.products.push({})
        },
        removeProductRow(index) {
            this.orders.products.splice(index, 1)
        },
        postOrder(event) {
            event.preventDefault()

            axios.post('http://api.faberlic.ostroleka.pl/order', this.orders)
                .then((response) => {
                    swal('Dziękuję!', `Twój numer zamówienia to: ${response.orderNumber}.`, 'success')
                    console.log(`Response: ${response.orderNumber}`)
                }).catch((err) => {
                    swal("Upss", "Przepraszam, coś poszło nie tak. Spróbuj proszę później.", "warning")
                    console.log(`Problem: ${err}`)
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
    input {
        margin-left: 5rem;
        padding: 1rem 0;
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
            border: none;
        }
    }

    .form-column {
        display: flex;
        flex-direction: column;
        padding-top: 15rem;
        
        label {
            margin: 1rem 0;
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

        button.add-row {
            display: inline-block;
            margin: 1rem 5rem;
            padding: 1rem 2rem;
            border: 1px solid #ccc;
            background-color: #fff;
            width: 15rem;
            cursor: pointer;
        }

        button.remove-row {
            display: flex;
            justify-content: center;
            align-items: center;
            width: 3rem;
            height: 3rem;
            border: none;
            background-color: transparent;
            font-size: 3rem;
            color: #f64747;
            cursor: pointer;
            outline: none;
        }
    }

    button.btn-order {
        margin: 10rem 0;
        border: none;
        outline: none;
        cursor: pointer;
    }
}

.form-row {
    display: flex;
    justify-content: flex-start;
    align-items: center;

    input {
        margin: 1rem;
        padding-left: 1rem;
        font-size: 2rem;
        border: 1px solid #ccc;

        &:focus {
            border: 1px solid #ccc;
        }

        &:first-child {
            flex-grow: 2;
        }
    }
}

@media screen and (max-width: 1140px) {
    .order-form-wrapper {
        padding: 0 2rem;
    }
}

@media screen and (max-width: 768px) {
    .form-column label span,
    .form-column label i {
        display: none;
    }

    .form-column {
        align-items: center;
    }

    .form .form-column label {
        text-align: center;
        font-size: 1.8rem;
    }

    .form input {
        font-size: 2.5rem;
    }

    .form-row {
        flex-direction: column;
    }

    .form {
    display: flex;
    flex-direction: column;
    align-items: center;
    }
}
</style>

