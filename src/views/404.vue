<template>
    <div class="page-not-found">
        <div class="four">
            <p class="four__item">4</p>
            <p class="four__item">0</p>
            <p class="four__item">4</p>
        </div>
        <p class="four-title">Taka strona nie istnieje.</p>
    </div>
</template>

<style lang="scss">
.page-not-found {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    width: 100%;
    height: calc(100vh - 18.5rem);
    font-weight: bold;
}

.four {
    display: flex;
}

p.four__item {
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 1rem;
    width: 10rem;
    height: 10rem;
    background-color: #ccc;
    border-radius: 10%;
    font-size: 5rem;
}

.four-title {
    margin-top: 1rem;
    font-size: 2rem;
}
</style>