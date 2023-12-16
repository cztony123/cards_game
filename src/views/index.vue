<template>
    <div class="box"><!-- transform: rotate(-90deg) scale(0.95); -->
        <div class="top">
            <div v-for="(item, index) in listDataTop" :key="index">
                <img :src="require(`../assets/cards-img/${item}.png`)"/>
            </div>
        </div>
        <div class="left">
            <div v-for="(item, index) in listDataLeft" :key="index">
                <img :src="require(`../assets/cards-img/${item}.png`)"/>
            </div>
        </div>
        <!-- <div class="right">
            <div>
                <ul v-for="(item, index) in listDataRight" :key="index">
                    <li><img :src="require(`../assets/cards-img/${item}.png`)"/></li>
                </ul>
            </div>
        </div> -->
        <!-- <div class="bottom">
            <div>
                <ul v-for="(item, index) in listDataBottom" :key="index">
                    <li><img :src="require(`../assets/cards-img/${item}.png`)"/></li>
                </ul>
            </div>
        </div> -->
        
        <button class="btn" @click="handleButton()">开始</button>
    </div>
</template>

<!-- const pai = {
    type:'heitao',
    value: 1  
}

cosnt arr = [..pai]

arr.sort((a, b) => a.value > b.value) -->

<script>
export default {
    data() {
        return {
            listDataTop: [],
            listDataLeft: [],
            listDataRight: [],
            listDataBottom: [],
        }
    },
    methods: {
        handleButton(){
            //为数组添加52个
            let arry = new Array(52).fill(0)
            let i = 0
            arry = arry.map(()=>{
                return i++
            })
            //打乱数组排序
            arry.sort(()=>Math.random() - 0.5)

            //截取数组前13个
            this.listDataTop = arry.splice(0,13)
            this. listDataLeft = arry.splice(0,13)
            this. listDataRight = arry.splice(0,13)
            this. listDataBottom = arry.splice(0,13)
            // const pai = [
            //     {
            //         type:'方块A',
            //         value: 0  
            //     },
            //     {
            //         type:'fangkuai_2',
            //         value: 1 
            //     },
            // ]
            this.listDataTop.sort(
                function(a, b){
                    return a - b
                }
            )

            
            console.log(this.listDataTop)
            console.log(this. listDataLeft)
            console.log(this. listDataRight)
            console.log(this. listDataBottom)
        }
    }
}
</script>

<style lang="scss" scope>
*{margin: 0;padding: 0;}
html,body {
    height:100%; 
} 
.box {
    position: relative;
    background-image: url(../assets/cards-img/bg.jpg);
    background-repeat: no-repeat;
    background-size: 100% 100%;
    width: 100%;
    height:100%; 
}
.top{
    display: flex;
    margin: auto;
    width: 76%;
    border: 1px solid red;
    div{
        width: 7.69%;
        img{
            width: 100%;
        }
    }
}

.left{
    position: absolute;
    display: flex;
    flex-direction:column;
    justify-content:space-between;
    top: 50%;
    left: 2%;
    transform: translate(0, -50%);
    margin: auto;
    width: 9%;
    height: 70%;
    border: 1px solid red;
    div{
        position: relative;
        width: 100%;
        height: 10px;
        text-align: center;
        border: 1px solid red;
        img{
            margin-top:-20px;
            width: 70%;
            transform: rotate(-270deg);
        }
    }
}

.bottom{
    position: absolute;
    bottom: 0;
    left: 50%;
    transform: translate(-50%, 0);
    display: flex;
    margin: auto;
    width: 76%;
    border: 1px solid red;
    div{
        
        width: 7.69%;
        img{
            
            width: 100%;
            
        }
    }
}
.btn{
    position: absolute;
    left: 50%;
    top:70%;
    width:80px;
    height:30px;
    background: #1991EB;
    border-radius: 5px;
    font-size: 18px;
    font-weight:600;
    margin-left: -40px;
    cursor: pointer;
}
</style>