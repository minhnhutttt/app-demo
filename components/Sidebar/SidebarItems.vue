<template>
    <ul :class="[{ 'is-show': isShow }, 'c-items']">
        <SidebarItem title="Getting started">
            <SidebarSub>
                <SidebarSubItem title="Installing the Cardano node" href="/getting-started/installing-the-cardano-node" />
                <SidebarSubItem title="Using the command line interface" href="/getting-started/use-cli" />
                <SidebarSubItem title="About stake pools, operators, and owners" href="/getting-started/about-stake-pools" />
            </SidebarSub>
        </SidebarItem>
        <SidebarItem title="New to Cardano"></SidebarItem>
        <SidebarItem title="Learn"></SidebarItem>
    </ul>
</template>
<script>
    export default {
        props: {
            isShow: {
                type: Boolean,
                default: () => false
            }
        }
    }
</script>
<style scoped>
    
    @media screen and (min-width: 769px) {
        .c-items {
            padding-top: 50px;
            display: block !important;
        }
    }
    @media screen and (max-width: 768px) {
        .c-items {
            background-color: #fff;
            padding: 20px 0;
            display: none;
        }
        .is-show {
            display: block;
        }
    }
</style>