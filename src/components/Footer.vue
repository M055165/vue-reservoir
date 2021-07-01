<template>
    <div id='myFooter'>
        <div class="myCard">
            <p>Create by Eddie</p>
        </div>
    </div>
</template>

<style lang="scss" scoped>
    #myFooter {
        height: 30vh;
        width: 100%;
        background-image: url('../../public/assets/footer.jpeg');
        background-size: cover;
        background-position: center center;
        background-repeat: no-repeat;
        position: relative;
        filter: blur(1.2px);
    }
    .myCard {
        position: absolute;
        width: 30%;
        height: 55%;
        background-color: rgba($color: #808080, $alpha: .4);
        left: 50%;
        top:50%;
        transform: translate(-50%,-50%);
        display: flex;
        justify-content: center;
        align-items: center;
    }
    p {
        font-size: 30px;
        font-weight: bold;
        font-style: italic;
    }
        @media screen and(max-width: 768px){
        .myCard{
            width: 60%;
            height: 45%;
        }
        p{
            font-size: 20px!important;
        }
    }
</style>