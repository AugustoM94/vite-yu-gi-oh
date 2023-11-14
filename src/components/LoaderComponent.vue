<template>
    <div>
        <img src="../assets/img/ZZ5H.gif" alt="loader-logo">
    </div>
</template>

<script>
    export default {
        name: 'LoaderComponent',    
    }
</script>

<style lang="scss" scoped>
div {
    position: absolute;
    top: 0;
    bottom: 0;
    left: 0;
    right: 0;
    z-index: 3000;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 30vw;
}
</style>