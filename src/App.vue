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
@import url('https://fonts.googleapis.com/css?family=Source+Sans+Pro');
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
    font-family: 'Source Sans Pro', sans-serif;
    font-size: 1.6rem;
    font-weight: 400;
    color: #333333;
    box-sizing: inherit;
}

h2 {
    margin: 5rem 0 0;
    font-family: 'Montserrat', sans-serif;
    font-size: 3rem;
    font-weight: 700;
    text-transform: uppercase;
}

h3 {
    margin: 2rem 0;
    font-family: 'Montserrat', sans-serif;
    font-size: 1.8rem;
    font-weight: 700;
    text-transform: uppercase;
}

// Helpers
.container {
    margin: 0 auto;
    width: 114rem;
}

p.subtitle {
    margin: 3rem 0;
    font-family: 'Montserrat', sans-serif;
    font-size: 1.6rem;
}

.btn-order {
    padding: 2rem 4rem;
    font-family: 'Montserrat', sans-serif;
    font-size: 1.8rem;
    font-weight: 700;
    color: #ffffff;
    text-decoration: none;
    text-transform: uppercase;
    background-color: #87d37c;
    border-radius: 10px;
    box-shadow: 2px 2px 4px rgba(0, 0, 0, .3);
    z-index: 10;

    &:hover {
        background-color: #76c26b;
    }
}
</style>
