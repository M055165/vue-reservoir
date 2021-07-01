<template>
    <div class="myContent" :id="place">
       <div class="container">
           <div class="header">
               <p><slot></slot></p>
           </div>
           <div class="row">
               <div class="col-md-12 col-lg-3  reservoir-items" v-for="(item,index) in reservoirData" :key="index">
                   <h1 class="reservoir_name">
                       {{item.name}}
                   </h1>
                   <div class="reservoir_graph">
                       <p class="rate">{{item.percentage}}%</p>
                       <div class="box">
                        <div class="wave" :style="{'--height':200-(percentageData[index]*4-200)+'%','--width':200-(percentageData[index]*4-200)+'%'}">
                            
                        </div>
                       </div>
                   </div>
                   <h2 class="reservoir_save">
                       有效蓄水量: {{item.volumn}}萬立方公尺{{percentageData[index]}}
                   </h2>
                   <h2 class="reservoir_in">
                       今日進水量：{{item.daliyInflow}}萬立方公尺
                   </h2>
                   <h2 class="reservoir_out">
                       今日出水量：{{item.daliyOverflow}}萬立方公尺
                   </h2>
                    <h2 class="reservoir_update">
                        更新時間：{{item.updateAt}}
                    </h2>
               </div>
             
           </div>
       </div>
    </div>
</template>

<style lang="scss" scoped>
    .myContent {
        padding-top:30px ;
        color:white;
        background-color: #1e3751;
    }
    .header {
        p {
        height: 30px;
        line-height: 30px;
        text-align: left;
        font-size: 30px;
        font-weight: bold;
    }
    }
    h1 {
        font-size: 24px;
    }
    h2 {
        font-size: 16px;
    }
    .reservoir-items{
        margin-bottom: 35px;
    }
    .reservoir_graph{
        width: 100%;
        display: flex;
        justify-content: center;
        margin:15px 0;
        position:relative;
    }
    .rate {
    color:#c9e4fe;
    font-size: 60px;
    font-weight: bold;
    position: absolute;
    z-index: 1000;
    left:50%;
    top:50%;
    transform: translate(-50%,-50%);
   }
    .box {
        overflow: hidden;
        width: 200px;
        height: 200px;
        border-radius: 50%;
        font-size: 35px;
        background-color: #808080;
        border:5px solid #dcdcdc;

    }
    .wave {
        width: 100%;
        height: 100%;
        border-radius: 50%;
        background-color: #4973ff;
        box-shadow:inset 0 0 50px rgba(0,0,0,0.5);
        position: relative;
    }
   
    .wave::before,.wave::after {
        content:'';
        position: absolute;
        width: var(--width);
        height: var(--height);
        top:0;
        left:50;
        transform: translate(-50%,-55%);
        background-color: #000;
    }
    .wave::before{
        border-radius: 80%;
        background-color: #808080;
        animation:animate 15s linear infinite;
    }
    .wave::after{
        border-radius: 40%;
        background-color: rgba(255,255,255,.5);
        animation:animate 12s linear infinite;
    }
    @keyframes animate {
        0%{
            transform : translate(-50%,-70%) rotate(0deg);
        }
      
        100% {
            transform :translate(-50%,-75%) rotate(360deg);
        }

    }
</style>

<script>
export default {
    props:['reservoirData','place','percentageData'],
    data(){
        return {
            reservoirPercentage:'',
            myReservoirData:[],
            abc:''
        }
    },

    

}

</script>