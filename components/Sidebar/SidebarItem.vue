<template>
    <li class="c-item">
        <a @click="() => isMenuOpen = !isMenuOpen" class="c-itemHeading">{{title}}<button aria-label="collapse" class="collapser">
            <svg v-if="isMenuOpen" xmlns="http://www.w3.org/2000/svg" width="12" height="12" viewBox="0 0 24 24"><path d="M7.33 24l-2.83-2.829 9.339-9.175-9.339-9.167 2.83-2.829 12.17 11.996z"></path></svg>
            <svg v-else xmlns="http://www.w3.org/2000/svg" width="12" height="12" viewBox="0 0 24 24"><path d="M0 7.33l2.829-2.83 9.175 9.339 9.167-9.339 2.829 2.83-11.996 12.17z"></path></svg>
            </button>
        </a>
        <div v-if="isMenuOpen">
            <slot />
        </div>
    </li>
</template>
<script>
    export default {
        props: {
            title: {
                type: String,
                default: () => ''
            }
        },
        data() {
            return {
                isMenuOpen: false
            }
        }
    }
</script>
<style scoped>
    .c-itemHeading {
        cursor: pointer;
        font-size: 16px;
        padding: 7px 35px 7px 15px;
        display: flex;
        align-items: center;
        position: relative;
        font-weight: bold;
    }
    
    @media screen and (min-width: 769px) {
        .c-itemHeading:hover {
            background-color: rgba(0,51,173,1);
            color: #fff;
        }
    }
    .collapser {
        background: transparent;
        border: none;
        outline: none;
        position: absolute;
        right: 20px;
        z-index: 1;
        cursor: pointer;
    }
    .collapser svg path {
        fill: #dcdcdc !important;
    }
</style>