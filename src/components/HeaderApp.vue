<script>
export default {

    name: 'HeaderApp',

    data () {
        return{

        }
    }

}
</script>

<template>

    <header>
        <div class="container d-flex align-items-center">
            <img src="../img/header_logo.jpg" alt="header_logo" class="me-3">
            <h3>Yu Gi Oh Cards</h3>
        </div>
    </header>
 
</template>

<style lang="scss">

header{
    background-color: white;
    height: 40px;
    position: fixed;
    width: 100%;
    z-index: 20;

    div{
        height: 100%;

        img{
            height: 100%;
        }
    }
}

</style>
