<template>
    <footer>
        <p>Copyright &copy; {{ getFullYear() }} Faberlic Zenobia Bednarowicz</p>
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
    justify-content: center;
    align-items: center;
    height: 6rem;
    font-size: 1.4rem;
    color: #666666;
    background-color: #000000;

    p {
        text-align: center;
    }
}
</style>
