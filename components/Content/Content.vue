<template>
    <div class="content">
        <slot />
    </div>
</template>

<style scoped>
    .content {
        margin: 3rem 88px;
        flex-grow: 1;
    }
    @media screen and (max-width: 768px) {
        .content {
            margin: 0 10px;
            padding-top: 3rem;
            flex: auto;
        }
    }


</style>