<template>
    <li class="c-item"><NuxtLink :to="href">{{title}}</NuxtLink></li>
</template>

<script>
    export default {
        props: {
            title: {
                type: String,
                default: () => ''
            },
            href: {
                type: String,
                default: () => ''
            }
        }
    }
</script>
<style scoped>
    .c-item {
        margin-left: 16px;
    }
    .c-item > a {
        cursor: pointer;
        color: #1d1e21;
            -webkit-text-decoration: none;
        text-decoration: none;
        display: -webkit-box;
        display: -webkit-flex;
        display: -ms-flexbox;
        display: flex;
        -webkit-align-items: center;
        -webkit-box-align: center;
        -ms-flex-align: center;
        align-items: center;
        position: relative;
        width: 100%;
        font-size: 14px;
        font-weight: 500;
        line-height: 1.5;
        padding: 7px 35px 7px 15px;
        border-style: none none none solid;
        border-width: 1px 0px 1px 1px;
        border-color: transparent currentcolor transparent transparent;
    }

    @media screen and (min-width: 769px) {
        .c-item > a:hover {
            background-color: rgba(0,51,173,1);
            color: #fff;
        }
    }
</style>