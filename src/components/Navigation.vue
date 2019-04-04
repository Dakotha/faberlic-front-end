<template>
    <header class="navigation-wrapper">
        <nav class="navigation-top container">
            <div class="navigation-top__logo">
                <a href="/">
                    <span>Faberlic</span><span class="navigation-top__logo-dot"></span>Zenobia Bednarowicz
                </a>
            </div>

            <div class="navigation-top__menu">
                <router-link to="/">Strona główna</router-link>
                <router-link to="#newsletter">Newsletter</router-link>
                <router-link to="/zamowienie">Złóż zamówienie</router-link>
            </div>
        </nav>
    </header>
</template>

<style lang="scss">
.navigation-wrapper {
    background-color: #ffffff;
    // box-shadow: 1px 1px 6px rgba(0, 0, 0, .05);
}

.navigation-top {
    display: flex;
    justify-content: space-between;
    align-items: center;
    height: 7rem;


    &__logo {
        a {
            font-size: 1.8rem;
            text-decoration: none;
            color: #333333;
        }

        span:first-child {
            font-size: 2rem;
            font-weight: 700;
        }

        &-dot {
            display: inline-block;
            margin: 0 .3rem;
            width: .5rem;
            height: .5rem;
            background-color: #f64747;
        }
    }

    &__menu {
        display: flex;

        a {
            font-size: 1.4rem;
            font-weight: 700;
            color: #666666;
            text-transform: uppercase;
            text-decoration: none;

            &:not(:last-child) {
                margin-right: 3rem;
            }

            &:hover {
                color: #333333;
            }

            &.router-link-exact-active {
                color: #333333;
            }
        }
    }
}
</style>

