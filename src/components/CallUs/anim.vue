<template>
    <div class="anim_container" v-scroll-reveal.reset="{delay:500,scarle:2}">
        
            <div class="icon icon_phone" ></div>

            <div class="plus one" >+</div>

            <div class="icon icon_delivery" ></div>

            <div class="plus">=</div>

            <div class="icon icon_pizza" ></div>

    </div>
</template>

<script>

    export default {
    }


</script>

<style>
    .anim_container {
        position:relative;
        display: flex;
        justify-content: space-between;
        flex-wrap: wrap;
    }

    .icon {
        background-size: cover !important;
        /* position: absolute; */
    }

    .plus {
        /* position: absolute; */
        font-size:160px;
        color:#ffffff;
        /* top: 60px; */
        margin-top:60px;
    }

    .icon_phone {
        background: url('../../assets/images/icons/icon-phone.png');
        width:130px;
        height:130px;
        top:30px
    }

    .icon_delivery {
        background: url('../../assets/images/icons/icon-delivery.png');
        width:200px;
        height:200px;
    }


    .icon_pizza {
        background: url('../../assets/images/icons/icon-pizza.png');
        width:200px;
        height:200px;
    }

</style>