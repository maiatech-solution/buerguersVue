<template>

    <div id="main_banner">
        <h1>Burguers</h1>
    </div>
</template>

<script>
export default {
    name: 'Banner'
}

</script>

<style scoped>
    #main_banner{
        background-image: url('../../public/img/burger.jpg');
        background-position: 0 -250px;
        background-size: cover;
        height: 700px;
        width: 100%;
        display: flex;
        justify-content: flex-start;
        align-items: center;
    }

    #main_banner h1{
        color: #fff;
        text-align: center;
        font-size: 60px;
        background-color: #22222200;
        padding: 10px 40px;
        border-top: 2px solid #fcba03;
        border-bottom: 2px solid #fcba03;
        margin-left: 5%;
    }

</style>