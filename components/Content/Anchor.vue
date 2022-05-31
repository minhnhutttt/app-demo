<template>
    <div class="anchor e1eqkayb5">
        <aside class="anchorWrap e1y52jk20">
            <ul class="rightSideBarUL">
                <slot />
            </ul>
        </aside>
    </div>
</template>

<style scoped>

.anchor {
    flex: 0 0 15rem;
}
@media screen and (max-width: 768px) {
    .anchor {
        display: none;
    }
}
.anchorWrap {
    width: 100%;
    border-right: 1px solid #ede7f3;
    height: 100vh;
    overflow: auto;
    position: fixed;
    position: -webkit-sticky;
    position: -moz-sticky;
    position: -webkit-sticky;
    position: sticky;
    top: 0;
    background: #fff;
}
.anchorWrap .rightSideBarUL {
    margin-top: 32px;
}
.anchorWrap .rightSideTitle {
    font-size: 10px;
    line-height: 1;
    font-weight: 700;
    text-transform: uppercase;
    -webkit-letter-spacing: 1.2px;
    -moz-letter-spacing: 1.2px;
    -ms-letter-spacing: 1.2px;
    letter-spacing: 1.2px;
    padding: 7px 24px 7px 16px;
    border-left: 1px solid #e6ecf1;
    border-left-color: rgb(230,236,241);
    color: #1d1e21;
}
.anchorWrap .rightSideBarUL li {
    list-style-type: none;
    border-left: 1px solid #e6ecf1;
    border-left-color: rgb(230,236,241);
}
.anchorWrap .rightSideBarUL li a {
    display: block;
    font-size: 12px;
    font-weight: 500;
    line-height: 1.5;
    padding: 7px 24px 7px 16px;
    color: #1d1e21;
}
</style>