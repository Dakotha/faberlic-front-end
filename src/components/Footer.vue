<template>
    <footer>
        <p>Copyright &copy; {{ getFullYear() }} Faberlic Zenobia Bednarowicz</p>
        <a href="/Polityka_prywatnosci.pdf" target="_blank">Polityka prywatności</a>
    </footer>
</template>

<script>
export default {
    methods: {
        getFullYear() {
            return new Date().getFullYear()
        }
    }
}
</script>


<style lang="scss">
footer {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 6rem;
    font-size: 1.4rem;
    color: #666666;
    background-color: #000000;

    p {
        text-align: center;
    }

    a {
        color: #666666;
    }
}
</style>
