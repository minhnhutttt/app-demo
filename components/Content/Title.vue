<template>
    <div class="c-titleWrapper"><h1><slot /></h1></div>
</template>

<style scoped>
    .c-titleWrapper {
        display: -webkit-box;
        display: -webkit-flex;
        display: -ms-flexbox;
        display: flex;
        -webkit-align-items: center;
        -webkit-box-align: center;
        -ms-flex-align: center;
        align-items: center;
        padding-bottom: 40px;
        border-bottom: 1px solid rgb(230,236,241);
        margin-bottom: 32px;
    }
    h1 {
        font-size: 34px;
        line-height: 1.3;
        -webkit-flex: 1;
        -ms-flex: 1;
        flex: 1;
        margin-top: 0;
        padding-top: 0;
        color: #000;
        font-weight: bold;
    }
</style>