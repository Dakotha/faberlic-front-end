<template>
    <section class="contact-wrapper">
        <div class="contact container">
            <a href="tel:509388653" class="contact__phone"><i class="fas fa-phone"></i>+48 509 388 653</a>
            <a href="mailto:faberlic.bednarowicz@gmail.com" class="contact__email"><i class="fas fa-at"></i>faberlic.bednarowicz@gmail.com</a>
            <a href="https://www.facebook.com/Faberlic-Zenobia-Bednarowicz-2270446443192814/?eid=ARDnOhV8C6N-YKB99lpapHf_UriJJajRFXGhEx-x2ZO2UxqAdc0I74oKiUcPLdOMmOX44Y4XxMlbzF78" target="_blank" class="contact__facebook"><i class="fab fa-facebook-f"></i>faberlic-zenobia-bednarowicz</a>
        </div>
    </section>
</template>

<style lang="scss">
.contact-wrapper {
    background-color: #f64747;
}

.contact {
    display: flex;
    justify-content: space-around;
    align-items: center;
    height: 5rem;

    a {
        font-size: 1.4rem;
        color: #ffffff;
        text-decoration: none;
    }

    & i {
        margin: 0 1rem;
        font-size: 1.6rem;
    }
}
</style>
