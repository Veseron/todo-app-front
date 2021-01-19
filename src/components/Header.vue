<template>
    <div class="header" id="nav" v-click-outside="closeMenu">
        <div class="menu-toggler" @click="menuToggler()">
            <svg height="384pt" viewBox="0 -53 384 384" width="384pt" xmlns="http://www.w3.org/2000/svg"><path d="m368 154.667969h-352c-8.832031 0-16-7.167969-16-16s7.167969-16 16-16h352c8.832031 0 16 7.167969 16 16s-7.167969 16-16 16zm0 0"/><path d="m368 32h-352c-8.832031 0-16-7.167969-16-16s7.167969-16 16-16h352c8.832031 0 16 7.167969 16 16s-7.167969 16-16 16zm0 0"/><path d="m368 277.332031h-352c-8.832031 0-16-7.167969-16-16s7.167969-16 16-16h352c8.832031 0 16 7.167969 16 16s-7.167969 16-16 16zm0 0"/></svg>
        </div>
        <div class="header-logo">
            Todo App
        </div>
        <div>

        </div>
        
        <div class="menu" v-bind:class="{open: menuOpen}">
            <div class="close-menu" @click="menuToggler()">
                <svg version="1.1" id="Capa_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px"
                        viewBox="0 0 512.001 512.001" style="enable-background:new 0 0 512.001 512.001;" xml:space="preserve">
                    <g>
                        <g>
                            <path d="M284.286,256.002L506.143,34.144c7.811-7.811,7.811-20.475,0-28.285c-7.811-7.81-20.475-7.811-28.285,0L256,227.717
                                L34.143,5.859c-7.811-7.811-20.475-7.811-28.285,0c-7.81,7.811-7.811,20.475,0,28.285l221.857,221.857L5.858,477.859
                                c-7.811,7.811-7.811,20.475,0,28.285c3.905,3.905,9.024,5.857,14.143,5.857c5.119,0,10.237-1.952,14.143-5.857L256,284.287
                                l221.857,221.857c3.905,3.905,9.024,5.857,14.143,5.857s10.237-1.952,14.143-5.857c7.811-7.811,7.811-20.475,0-28.285
                                L284.286,256.002z"/>
                        </g>
                    </g>
                </svg>
            </div>
            <div class="menu-link">
                <router-link to="/">Home</router-link>
            </div>
            <div class="menu-link">
                <router-link to="/todos">Todos</router-link>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            menuOpen: false,
        }
    },
    methods: {
        menuToggler() {
            console.log('ok')
            this.menuOpen = !this.menuOpen
        },
        closeMenu() {
            this.menuOpen = false
        }
    },
}
</script>

<style lang="scss">

.header {
    min-height: 30px;
    background-color: rgb(56, 148, 56);
    padding: 10px 15px;
    margin-bottom: 25px;
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.menu-toggler {
    cursor: pointer;
    svg {
        width: 32px;
        height: 32px;

        path {
            fill: #fff;
        }
    }
}

.header-logo {
    color: #fff;
    font-size: 22px;
    font-weight: 600;
    margin-left: -24px;
}

.menu {
    position: fixed;
    width: 35%;
    background-color: #fff;
    top: 0;
    left: -50%;
    height: 100vh;
    box-shadow: 6px 0px 12px -3px rgba(0,0,0,0.57);
    padding: 15px;
    display: flex;
    flex-direction: column;
    padding-top: 40px;
    transition: ease-in-out .4s;
    opacity: 0;

    .menu-link {
        text-align: left;
        padding: 15px;
        border-bottom: 1px solid rgb(46, 44, 44);

        a {
            color: #000;
            text-decoration: none;
            width: 100%;
            display: block;
        }
    }

    &.open {
        opacity: 1;
        left: 0;
    }
}
@media screen and (min-width: 991px) {
    .menu {
        width: 20%;
    }
}
.close-menu {
    position: absolute;
    top: 15px;
    right: 15px;
    cursor: pointer;
    svg {
        width: 24px;
        height: 24px;
        path {
            fill: #000;
        }
    }
}
</style>