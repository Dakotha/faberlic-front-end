<template>
    <section class="contact-wrapper">
        <div class="contact container">
            <div class="contact__phone"><i class="fas fa-phone"></i>+48 509 388 653</div>
            <div class="contact__email"><i class="fas fa-at"></i>faberlic.bednarowicz@gmail.com</div>
            <div class="contact__facebook"><i class="fab fa-facebook-f"></i>faberlic-zenobia-bednarowicz</div>
        </div>
    </section>
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
</style>
