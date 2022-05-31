<template>
    <div class="c-sidebar">
        <SidebarItems :isShow="isShow" />
        <div class="toggle" @click="() => isShow = !isShow">
            <div class="navBarDefault removePadd"><span class="navBarToggle" role="button" tabindex="0">
                <span class="iconBar"></span><span class="iconBar"></span><span class="iconBar"></span></span>
            </div>
        </div>
    </div>
</template>
<script>
    export default {
        data() {
            return {
                isShow: false
            }
        }
    }
</script>
<style scoped>
.c-sidebar {
    width: 20rem;
    height: 100vh;
    overflow: auto;
    position: fixed;
    padding-left: 0px;
    position: -webkit-sticky;
    position: -moz-sticky;
    position: -webkit-sticky;
    position: sticky;
    top: 0;
    padding-right: 0;
    border-right: 1px solid rgba(0, 0, 0, 0.1);
}

@media screen and (max-width: 768px) {
    .c-sidebar {
        width: 100%;
        height: auto;
        border-right: 0;
        position: relative;
        overflow: hidden;
        background: rgba(0, 51, 173, 1);
        padding: 20px;
    }
}
@media screen and (min-width: 769px) {
    .toggle {
        display: none;
    }
}
.toggle {
    height: 60px;
    box-shadow: 0 3px 6px 0 rgb(0 0 0 / 16%);
    background-color: #f8f8f8;
    position: relative;
    cursor: pointer;
}
.navBarToggle {
    border: 0px solid #fff;
    border-radius: 4px;
    width: 36px;
    height: 33px;
    position: absolute;
    right: 20px;
    padding: 8px 5px;
    margin-right: 0;
    display: block;
    position: absolute;
    left: 11px;
    top: 15px;
    background: #fff;
}
.navBarToggle .iconBar {
    display: block;
    width: 22px;
    height: 2px;
    border-radius: 1px;
    margin: 0 auto;
    margin-top: 4px;
    background-color: rgba(0,51,173,1);
}
</style>