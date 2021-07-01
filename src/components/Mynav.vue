<template>
<div id="myNav">
    <img src="../../public/assets/top.jpeg" alt="">
    <div class="header">
        <div class="title">
            <h1>台灣水庫即時水情</h1>
            <h2>使用經濟部水利署 Open Data 即時呈現各水庫資訊</h2>
            <h2>全民防疫，台灣加油！！</h2>
        </div>
        <ul class="choose">
            <li><a href="#north">北部</a></li>
            <li><a href="#mid">中部</a></li>
            <li><a href="#south">南部</a></li>
        </ul>
    </div>
</div>
</template>

<style lang="scss" scoped>
#myNav {
    height: 55vh;
    width: 100%;
    position: relative;
    color: white;
    letter-spacing: 1.3px;
}

img {
    width: 100%;
    height: 100%;
    filter: blur(3px);
}

.header {
    width: 100%;
    position: absolute;
    left: 50%;
    top: 50%;
    transform: translate(-50%, -50%);
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;

    .title {
        display: flex;
        flex-direction: column;

        h1 {
            font-size: 45px;
        }

        h2 {
            margin-top: 13px;
            font-size: 15px;
        }
    }
}

ul {
    margin-top: 20px;
    list-style: none;
    display: flex;

    li {
        display: block;
        background: #ffc000;
        color: #202529;
        margin: 10px;
        border-radius: 5px;
        cursor: pointer;
        padding: 12px;
        a {
            color: #202529;
            text-decoration: none;
        }
    }
}
</style>
