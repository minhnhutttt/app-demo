<template>
    <header class="c-header">
        <NuxtLink to="/" class="c-logo">
            Logo
        </NuxtLink>
    </header>
</template>

<style scoped>
/* Header */

.c-header {
    height: 80px;
    display: flex;
    align-items: center;
    background: rgba(0,51,173,1);
    padding: 0 20px;
}

.c-logo {
    color: #fff;
    font-size: 36px;
    font-weight: bold;
    text-transform: uppercase;
}
</style>