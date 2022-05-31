<template>
    <div class="posts">
        <div class="postsWrap">
            <NuxtLink v-if="prevTitle !== ''" class="previousBtn" :to="prevLink">
            <div class="leftArrow"><svg preserveAspectRatio="xMidYMid meet" height="1em" width="1em" fill="none"
                    xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" stroke-width="2" stroke-linecap="round"
                    stroke-linejoin="round" stroke="currentColor" class="_13gjrqj">
                    <g>
                        <line x1="19" y1="12" x2="5" y2="12"></line>
                        <polyline points="12 19 5 12 12 5"></polyline>
                    </g>
                </svg></div>
            <div class="preRightWrapper">
                <div class="smallContent"><span>Previous</span></div>
                <div class="nextPreviousTitle"><span>{{prevTitle}}</span></div>
            </div>
            </NuxtLink>
            <NuxtLink v-if="nextTitle !== ''" class="nextBtn" :to="nextLink">
                <div class="nextRightWrapper">
                    <div class="smallContent"><span>Next</span></div>
                    <div class="nextPreviousTitle"><span>{{nextTitle}}</span></div>
                </div>
                <div class="rightArrow"><svg preserveAspectRatio="xMidYMid meet" height="1em" width="1em" fill="none"
                        xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" stroke-width="2" stroke-linecap="round"
                        stroke-linejoin="round" stroke="currentColor" class="_13gjrqj">
                        <g>
                            <line x1="5" y1="12" x2="19" y2="12"></line>
                            <polyline points="12 5 19 12 12 19"></polyline>
                        </g>
                    </svg></div>
            </NuxtLink>
        </div>
    </div>
</template>
<script>
    export default {
        props: {
            nextTitle: {
                type: String,
                default: () => ''
            },
            nextLink: {
                type: String,
                default: () => ''
            },
            prevTitle: {
                type: String,
                default: () => ''
            },
            prevLink: {
                type: String,
                default: () => ''
            }
        }
    }
</script>
<style scoped>
.posts {
    padding: 50px 0;
}   
.postsWrap {
    margin: 0px;
    padding: 0px;
    width: auto;
    display: grid;
    grid-template-rows: auto;
    -webkit-column-gap: 24px;
    column-gap: 24px;
    grid-template-columns: calc(50% - 8px) calc(50% - 8px);
}
@media screen and (max-width: 768px) {
    .postsWrap {
        display: block;
        -webkit-column-gap: 24px;
        column-gap: 24px;
        grid-template-columns: calc(50% - 8px) calc(50% - 8px);
    }
}
.postsWrap .previousBtn ,
.postsWrap .nextBtn{
    cursor: pointer;
    -moz-box-align: center;
    -moz-box-direction: normal;
    -moz-box-orient: horizontal;
    margin: 0px;
    padding: 0px;
    position: relative;
    display: -webkit-box;
    display: -webkit-flex;
    display: -ms-flexbox;
    display: flex;
    -webkit-flex-direction: row;
    -ms-flex-direction: row;
    flex-direction: row;
    -webkit-align-items: center;
    -webkit-box-align: center;
    -ms-flex-align: center;
    align-items: center;
    place-self: stretch;
    border-radius: 3px;
    border: 1px solid rgb(230,236,241);
    -webkit-transition: border 200ms ease 0s;
    transition: border 200ms ease 0s;
    box-shadow: rgb(0 0 0 / 10%) 0px 3px 8px 0px;
    -webkit-text-decoration: none;
    text-decoration: none;
    background-color: #fff;
    color: #1d1e21;
}

@media screen and (max-width: 768px) {
    .postsWrap .previousBtn {
        margin-bottom: 20px;
    }
}
.postsWrap .leftArrow {
    display: block;
    margin: 0px;
    color: rgb(157,170,182);
    -webkit-flex: 0 0 auto;
    -ms-flex: 0 0 auto;
    flex: 0 0 auto;
    font-size: 24px;
    -webkit-transition: color 200ms ease 0s;
    transition: color 200ms ease 0s;
    padding: 16px;
    padding-right: 16px;
}
.postsWrap .rightArrow {
    -webkit-flex: 0 0 auto;
    -ms-flex: 0 0 auto;
    flex: 0 0 auto;
    font-size: 24px;
    -webkit-transition: color 200ms ease 0s;
    transition: color 200ms ease 0s;
    padding: 16px;
    padding-left: 16px;
    display: block;
    margin: 0px;
    color: rgb(157,170,182);
}
.nextRightWrapper {
    display: block;
    margin: 0px;
    padding: 16px;
    -webkit-flex: 1 1 0%;
    -ms-flex: 1 1 0%;
    flex: 1 1 0%;
}
.preRightWrapper {
    display: block;
    margin: 0px;
    -webkit-flex: 1 1 0%;
    -ms-flex: 1 1 0%;
    flex: 1 1 0%;
    padding: 16px;
    text-align: right;
}
.smallContent {
    display: block;
    margin: 0px;
    padding: 0px;
    color: #6e6e6e;
}
.smallContent span {
    font-size: 12px;
    line-height: 1.625;
    font-weight: 400;
}
.postsWrap .nextPreviousTitle {
    display: block;
    margin: 0px;
    padding: 0px;
    -webkit-transition: color 200ms ease 0s;
    transition: color 200ms ease 0s;
}
.postsWrap .nextPreviousTitle span {
    font-size: 16px;
    line-height: 1.5;
    font-weight: 500;
}
</style>