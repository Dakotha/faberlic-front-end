<template>
    <main id="home">

        <section class="contact-wrapper">
            <div class="contact container">
                <div class="contact__phone"><i class="fas fa-phone"></i>+48 509 388 653</div>
                <div class="contact__email"><i class="fas fa-at"></i>faberlic.bednarowicz@gmail.com</div>
                <div class="contact__facebook"><i class="fab fa-facebook-f"></i>faberlic-zenobia-bednarowicz</div>
            </div>
        </section>
        
        <section class="order">
            <div class="order__bg"></div>
            <!-- <a href="/zamowienie">Złóż zamówienie</a> -->
            <router-link to="/zamowienie" class="btn-order">Złóż zamówienie</router-link>
        </section>

        <section class="how-wrapper">
            <div class="how container">

                <h2>Jak złożyć zamówienie?</h2>
                <p class="subtitle">Zamówienie złożysz w trzech prostych krokach. Najedź kursorem na kafelek poniżej, aby przeczytać więcej informacji.</p>

                <div class="how__box-wrapper">
                    <div class="how__box">
                        <div class="how__box-counter">1</div>

                        <div class="how__box-front">
                            <h3>Kliknij przycisk "Złóź zamówienie"</h3>
                            <i class="fas fa-directions"></i>
                        </div>

                        <div class="how__box-back">
                            <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quibusdam facere veniam officiis dolorem excepturi inventore laborum? Autem nesciunt, quos architecto, cum accusantium iste modi quasi, provident aspernatur adipisci veritatis corporis?</p>
                        </div>
                    </div>

                    <div class="how__box">
                        <div class="how__box-counter">2</div>

                        <div class="how__box-front">
                            <h3>Wypełnij prosty formularz</h3>
                            <i class="fas fa-directions"></i>
                        </div>

                        <div class="how__box-back">
                            <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quibusdam facere veniam officiis dolorem excepturi inventore laborum? Autem nesciunt, quos architecto, cum accusantium iste modi quasi, provident aspernatur adipisci veritatis corporis?</p>
                        </div>
                    </div>

                    <div class="how__box">
                        <div class="how__box-counter">3</div>

                        <div class="how__box-front">
                            <h3>Potwierdź złożenie zamówienia</h3>
                            <i class="fas fa-directions"></i>
                        </div>

                        <div class="how__box-back">
                            <p>Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quibusdam facere veniam officiis dolorem excepturi inventore laborum? Autem nesciunt, quos architecto, cum accusantium iste modi quasi, provident aspernatur adipisci veritatis corporis?</p>
                        </div>
                    </div>
                </div>

                <img src="../assets/img/how-arrow.png" alt="Złóż zamówienie">
                <router-link to="/zamowienie" class="btn-order">Złóż zamówienie</router-link>

            </div>
        </section>

        <section class="newsletter">

            <h2>Zapisz się na newsletter</h2>
            <p class="subtitle">Dzięki newsletter'owi zawsze na czas dowiesz się o nowych produktach, katalogach i wydarzeniach.</p>

            <input type="text" placeholder="Wpisz swój adres email">
        </section>

    </main>
</template>

<style lang="scss">
// Contact section
.contact-wrapper {
    background-color: #f64747;
}
.contact {
    display: flex;
    justify-content: space-around;
    align-items: center;
    font-family: 'Montserrat', sans-serif;
    font-size: 1.4rem;
    color: #ffffff;
    height: 5rem;

    & i {
        margin: 0 1rem;
        font-size: 1.6rem;
    
    }
}
// End of Contact section


// Order section
.order {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 30rem;

    position: relative;
    // Photo by rawpixel.com from Pexels
    background: url('../assets/img/order-bg.jpg');
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
// End of Order section


// How section
.how-wrapper {
    padding-top: 5rem;
    background-color: rgba(0, 0, 0, .05);
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
        height: 30rem;
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
            font-family: 'Montserrat', sans-serif;
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
        top: 80%;
        left: 20rem;
        width: 213px;
        height: 80px;
    }

    & a {
        margin: 5rem 0;
    }
}
// End of How section


// Newsletter section
.newsletter {
    display: flex;
    flex-direction: column;
    justify-content: flex-start;
    align-items: center;
    height: 50rem;
    padding-top: 8rem;

    input {
        margin-top: 5rem;
        padding: 2rem;
        height: 5rem;
        width: 40rem;
    }
}
// End of Newsletter section
</style>

