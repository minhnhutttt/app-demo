<template>
    <div class="contentWrap">
        <slot />
    </div>
</template>

<style scoped>
    @media screen and (min-width: 769px) {
        .contentWrap {
            display: flex;
            flex: 1;
        }
    }
</style>