<template>

<!-- v-fi 조건식이 참일때만 보임 -->
<div class="black-bg" v-if="모달창열렸니 == true" @click="모달창열렸니=false">
  <div class="white-bg">
    <h4>상세페이지임</h4>
    <p>상세페이지 내용임</p>
    <button @click="모달창열렸니=true">닫기</button>
  </div>
</div>


<div>
  <!-- <img alt="Vue logo" src="./assets/logo.png" style="width : 50px, align : left"> -->

  <div class="menu">
    <!-- <a>Home</a>
    <a>Products</a>
    <a>About</a> -->
    <a v-for="test in 메뉴들" :key ="test">{{ test }}</a>
    <a v-for="(a,i) in 메뉴들" :key ="i">{{ 신고수[i] }}</a>
  </div>






  <div>
    {{logo}}
    <!-- <h4 class="red" :style="스타일">XX 원룸</h4> -->
    <!-- <p>{{ price1 }} 만원</p> -->
  </div>

  <div v-for="(tt,i) in 원룸들" :key="i">
    <!-- <img v-bind:src = "sample[i]" class="room-img" @click="모달창열렸니=true">  -->
    <img v-bind:src = "tt.image" class="room-img" @click="모달창열렸니=true"> 
    <!-- <h4 @click="모달창열렸니=true">{{tt}}</h4> -->
    <h4 @click="모달창열렸니=true">{{tt.title}}</h4>


    <!-- 이미지 경로 테스트 -->
    <!-- <img src = "@/assets/room0.jpg" class="room-img"> -->
    <!-- <img src = "https://i.imgur.com/cOjXgoi.gif"> -->
    <!-- <img v-bind:src = "giff" class="room-img"> -->

    <!-- <p>{{ (i+1)*20 }} 만원</p> -->
    <p>{{ tt.price }} 만원</p>
    <button @click="increase(i)">허위매물 신고 </button>   
    <span> 신고수 : {{신고수[i]}}</span>
  </div>

  <br>

  <button @click="check()"> 변수 확인 </button>
  
<!-- 
  <div>
    <h4>{{products[0]}}</h4>
    {{price1}} 만원 
  </div>

  <div>
    <h4>{{products[1]}}</h4>
    {{price1}} 만원 
  </div>

  <div>
    <h4>{{products[2]}}</h4>
    {{price1}} 만원 
  </div> -->
</div>
</template>

<script>

// import oneroom from './assets/oneroom.js'
import {oneroom, 추가변수} from './assets/oneroom.js'

추가변수




export default {
  name: 'App',
  data(){
    return{

      // import 한 데이터
      // Array 안에 오브젝트로 들어있다.  
      //  
      원룸들 : oneroom,
      

      // UI 상태 데이터로 저장
      모달창열렸니 : false,
      
      신고수 : 추가변수.fill(0),
      // 신고수 : [0,0,0,0,0,0],

      price1 : 80,
      price2 : 70,
      logo : '원룸샵',
      스타일 : 'color : blue',
      메뉴들 : ['Home', 'Shop', 'About'],
      products : ['역삼동원룸', '천호동원룸', '마포구원룸'],
      sample : [require('@/assets/room0.jpg'), require('./assets/room1.jpg'), require('./assets/room2.jpg')],
      giff : 'https://i.imgur.com/cOjXgoi.gif'
    }
  },
  methods : {
    increase(i) {
      this.신고수[i] ++;
      console.log("신고수 증가");
    },
    check(){
      alert( this.신고수[0] +',' + this.신고수[1] + ','+ this.신고수[2])
    }
  },
  components: {
  }
}
</script>





<style>

img {
  cursor: pointer;
}
h4 {
  cursor: pointer;
}

body {
  margin: 0;
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%; height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed; padding: 20px;         
}
.white-bg {
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
}

.room-img{
  width: 100%;
  margin-top: 40px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /* margin-top: 60px; */
}
.menu {
  background: darkslateblue ;
  padding: 15px;
  border-radius:  5px;
}
.menu a {
  color:  white;
  padding: 10px;

}
</style>
