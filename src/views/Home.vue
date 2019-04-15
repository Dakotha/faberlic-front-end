<template>
    <main id="home">

        <section class="order">
            <div class="order__bg"></div>
            <router-link to="/zamowienie" class="btn-order">Złóż zamówienie</router-link>
        </section>

        <section class="how-wrapper">
            <div class="how container">

                <h2>Jak złożyć zamówienie?</h2>
                <p class="subtitle">Zamówienie złożysz w trzech prostych krokach.<br>Najedź kursorem myszy na kafelek poniżej, aby przeczytać więcej informacji.</p>

                <div class="how__box-wrapper">
                    <div class="how__box">
                        <div class="how__box-counter">1</div>

                        <div class="how__box-front">
                            <h3>Kliknij przycisk<br>"Złóż zamówienie"</h3>
                            <i class="fas fa-directions"></i>
                        </div>

                        <div class="how__box-back">
                            <p>Na stronie znajdują się aż trzy przyciski "Złóż zamówienie". Pierwszy znajdziesz w górnym menu strony. Drugi poniżej górnego menu, w dużej sekcji z banerem. I kolejny przycisk poniżej tego kafelka.</p>
                        </div>
                    </div>

                    <div class="how__box">
                        <div class="how__box-counter">2</div>

                        <div class="how__box-front">
                            <h3>Wypełnij prosty<br>formularz</h3>
                            <i class="fas fa-align-justify"></i>
                        </div>

                        <div class="how__box-back">
                            <p>Po kliknięciu w przycisk "Złóż zamówienie" zostaniesz przeniesiona na stronę z formularzem. Formularz jest dobrze opisany i wystarczy podążać za wskazówkami.</p>
                        </div>
                    </div>

                    <div class="how__box">
                        <div class="how__box-counter">3</div>

                        <div class="how__box-front">
                            <h3>Potwierdź złożenie<br>zamówienia</h3>
                            <i class="fas fa-paper-plane"></i>
                        </div>

                        <div class="how__box-back">
                            <p>Jest to bardzo ważna cześć. Po złożeniu zamówienia, program wyświetli nr tego zamówienia (numer zamówienia otrzymasz także na podany w formularzu adres email)<br>Skopiuj lub zapisz numer zamówienia i potwierdź zamówienie poprzez wysłanie tego numeru w wiadomości prywatnej na facebook'u lub w wiadomości email.</p>
                        </div>
                    </div>
                </div>

                <img src="../assets/img/how-arrow.png" alt="Złóż zamówienie">
                <router-link to="/zamowienie" class="btn-order">Złóż zamówienie</router-link>

            </div>
        </section>

        <section class="newsletter">

            <h2>Zapisz się na newsletter</h2>
            <p class="subtitle">Dzięki newsletter'owi zawsze na czas dowiesz się o nowych produktach, katalogach i wydarzeniach.<br>Podaj swój adres email, a wszystkie wiadomości będziesz otrzymywać prosto do skrzynki pocztowej.</p>

            <div class="newsletter__form">
                <input v-model="newsletter" type="email" placeholder="Wpisz swój adres email">
                <button @click="onNewsletter">Wyślij</button>
            </div>
        </section>

    </main>
</template>

<script>
import axios from '../axios'
import validator from 'validator'
import swal from 'sweetalert'

export default {
    data: function () {
        return {
            newsletter: ''
        }
    },

    methods: {
        onNewsletter() {
            if (!validator.isEmail(this.newsletter)) {
                swal({
                    title: 'Uwaga!',
                    text: 'Wygląda na to, że podałaś niewłaściwy adres email.',
                    icon: 'info'
                })

                return false
            }
            
            axios.post('/newsletter', { email: this.newsletter })
                .then(() => {
                    swal({
                        title: 'Dziękuję!',
                        text: 'Zapisałam Twój adres email.',
                        icon: 'success',
                        timer: 3000
                    });
                })
                .catch(err => {
                    swal({
                        title: 'Upss, Newsletter nie działa. Spróbuj proszę później.',
                        icon: 'warning',
                        timer: 3000
                    })
                    console.log(err)
                })
        }
    }
}
</script>


<style lang="scss">
// Order section
.order {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 40rem;

    position: relative;
    // Photo by rawpixel.com from Pexels
    background: url('../assets/img/faberlic-header.jpg');
    background-size: cover;
    background-position-y: 80%;

    &__bg {
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: rgba(0, 0, 0, .8);
    }
}

@media screen and (max-width: 768px) {
    .order {
        height: 20rem;
    }
}
// End of Order section


// How section
.how-wrapper {
    padding-top: 5rem;
    background-color: rgba(0, 0, 0, .05);
    border-bottom: 1px solid rgba(0, 0, 0, .04);
}

.how {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    position: relative;

    &__box-wrapper {
        display: flex;
        justify-content: center;
        width: 100%;
        margin-top: 10rem;
    }

    &__box {
        position: relative;
        height: 35rem;
        width: 33.333333%;
        perspective: 1000px;
        border-radius: 5px;
  
        &:not(:last-child) {
            margin-right: 5px;
        }

        &-counter {
            position: absolute;
            top: -5rem;
            left: 50%;
            transform: translateX(-50%);
            width: 8rem;
            height: 8rem;
            border-radius: 100%;
            box-shadow: 2px 2px 4px rgba(0, 0, 0, $alpha: .3);
            background-color: #f64747;
            display: flex;
            justify-content: center;
            align-items: center;
            font-size: 4rem;
            font-weight: 700;
            color: #ffffff;
            transition: background-color .3s ease-in-out, color .3s ease-in-out;
            z-index: 20;
        }

        &-front, &-back {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            display: flex;
            flex-direction: column;
            justify-content: space-around;
            align-items: center;
            padding: 1rem;
            text-align: center;
            backface-visibility: hidden;
            transition: transform .3s ease-in-out;
            transform-style: preserve-3d;
            border-radius: inherit;
            padding-top: 5rem;
        }

        &-front {
            background-color: #ffffff;

            & i {
                font-size: 10rem;
                color: #666666;
            }
        }

        &-back {
            padding: 3rem;
            font-size: 1.6rem;
            color: #ffffff;
            line-height: 2.4rem;
            background-color: #f64747;
            transform: rotateY(-180deg);
        }

        &:hover > &-front {
            transform: rotateY(180deg)
        }

        &:hover > &-back {
            transform: rotateY(0);
        }

        &:hover > &-counter {
            background-color: #ffffff;
            color: #666666;
        }
    }

    & img {
        position: absolute;
        top: 82%;
        left: 19rem;
        width: 213px;
        height: 80px;
    }

    & a {
        margin: 5rem 0;
    }
}

@media screen and (max-width: 960px) {
    .how__box-wrapper {
        flex-direction: column;
        align-items: center;
    }

    .how__box {
        margin-bottom: 10rem;
        width: 80%;
    }

    .how img {
        display: none;
    }
}
// End of How section


// Newsletter section
.newsletter {
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: center;
    padding-top: 8rem;
    margin-bottom: 10rem;

    &__form {
        display: flex;
        margin-top: 5rem;

        input {
            padding: 2rem;
            height: 5rem;
            width: 40rem;
            font-size: 1.6rem;
            outline: none;
        }

        button {
            margin-left: 1rem;
            padding: 1rem 2rem;
            height: 5rem;
            border: 1px solid #aaa;
            border-radius: .5rem;
            background-color: #fff;
            cursor: pointer;
            outline: none;

            &:hover {
                background-color: #eee;
            }
        }
    }
}

@media screen and (max-width: 900px) {
    .newsletter {
        padding: 0 2rem;
    }
}

@media screen and (max-width: 600px) {
    .newsletter__form input {
        width: 25rem;
    }
}

@media screen and (max-width: 400px) {
    .newsletter__form input {
        width: 20rem;
    }
}
// End of Newsletter section
</style>