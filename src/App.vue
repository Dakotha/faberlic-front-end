<template>
    <div id="app">
        <Navigation />
        <Contact />
        <router-view/>
        <Footer />
    </div>
</template>

<script>
import Navigation from '@/components/Navigation'
import Contact from '@/components/Contact'
import Footer from '@/components/Footer'

export default {
    components: { Navigation, Contact, Footer }
}
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css?family=Montserrat:400,700');

*,
*::before,
*::after {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

html {
    font-size: 62.5%;
}

body {
    font-family: 'Montserrat', sans-serif;
    font-size: 1.6rem;
    font-weight: 400;
    color: #333333;
    box-sizing: inherit;
}

h2 {
    margin: 5rem 0 0;
    font-size: 3rem;
    font-weight: 700;
    text-transform: uppercase;
    text-align: center;
}

h3 {
    margin: 2rem 0;
    font-size: 1.8rem;
    font-weight: 700;
    text-transform: uppercase;
    text-align: center;
}

p.subtitle {
    margin: 3rem 0;
    text-align: center;
    line-height: 2.4rem;
}

// Helpers
.container {
    margin: 0 auto;
    max-width: 114rem;
    // width: 114rem;
}

.btn-order {
    position: relative;
    padding: 2rem 6rem;
    font-size: 1.8rem;
    font-weight: 700;
    color: #ffffff;
    text-decoration: none;
    text-transform: uppercase;
    background-color: #87d37c;
    border: none;
    border-radius: 10px;
    box-shadow: 4px 8px 20px rgba(0, 0, 0, .25);
    z-index: 10;

    &:hover {
        background-color: #76c26b;
    }

    &:active {
        top: .3rem;
    }
}
</style>
