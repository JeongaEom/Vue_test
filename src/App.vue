<template>

<!-- 
동적인 UI 만드는 법 :

0. HTML CSS로 디자인
1.UI의 현재 상태를 데이터로 저장
2.데이터에 따라  UI가 어쩧게 보일지 작성

-->

<!-- 
  모달창 
  
  v-if=""
  v-if="조건식"
  - 조건식이 참(true)일때만 HTML 보여줌

-->
  <div class="black-bg" v-if="모달창열렸니 == true">
    <div class="white-bg">
      <h4>상세페이지임</h4>
      <p>상세페이지 내용임</p>
      <button @click="모달창열렸니 = false">닫기</button>
    </div>
  </div>

  <div class="black-bg"  v-if="모달창열렸니1 == true">
    <div class="white-bg">
      <h4>상세페이지임</h4>
      <p>상세페이지 내용임</p>
      <button @click="모달창열렸니1 = false">닫기</button>
    </div>
    <!-- <div class="white-bg" v-for="(a,i) in 원룸들" :key="i">
      <h4>{{ 원룸들[i].title }}</h4>
      <p>{{ 원룸들[i].content }}</p>
      <button @click="모달창열렸니 = false">닫기</button>
    </div> -->
  </div>


  <div class="menu">
    <!-- 
      반복문 쓸때 :key 안쓰면 에러남 

      Vue의 HTML 반복문

      1.기본형
      <태그 v-for="작명 in 몇회" :key="작명"></태그>
      예시)  
      <a v-for="작명 in 3" :key="작명">Home</a>

      2. * data 는 하단 javascript data(){ return{ 메뉴들 : [] }} 안에 있는 거
      <태그 v-for="작명 in data" :key="작명"></태그>
      예시) 
      <a v-for="작명 in 메뉴들" :key="작명">Home</a>
      <a v-for="a in 메뉴들" :key="a">{{ a }}</a>

      - 자료안의 데이터 갯수만큼 반복됨
      - 작명한 변수는 데이터 안의 자료가 됨

      3. 변수 작명 2개까지 가능 (a,i)
      예시) 
      <a v-for="(a,i) in 메뉴들" :key="a">{{ a }}</a>

      - 왼쪽 변수는 array내의 데이터
      - 오른쪽 변수는 1씩 증가하는 정수

    -->
    <a v-for="a in 메뉴들" :key="a">{{ a }}</a>
  </div>

  <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
  <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->

  <div>원룸샵1</div>
  <div v-for="d in 가격 " :key="d">
      <h4>{{ d.products1 }} 원룸</h4>
      <p>{{ d.price1 }} 만원</p>
  </div>
 
  <hr>

 <div>원룸샵2</div>
  <div v-for="(a,i) in products" :key="i">
      <h4>{{ products[i] }} 원룸</h4>
      <p>50만원</p>
  </div>

<hr>

  <div>원룸샵3</div>
  <div>
      <img alt="" src="./assets/images/room0.jpg" class="room-img"> 
      <h4 @click="모달창열렸니 = true">{{ products[0] }} 원룸</h4>
      <p>{{ price1 }} 만원</p>
      <!-- 
        버튼 눌렸을때 

        자바스크립트 실행하려면
        1. 전통방식은 
        onclick=""
        2. Vue방식은 
        v-on:click="" 
        v-on:click="javascript 함수 사용" 
        3. 또는 v-on:의 약자 @
        @click="" 
        @click="javascript 함수 사용" 

        v-on:click="신고수++" 에서 ++는 변수에 1 더해주는 문법
        v-on:click="신고수 +=1" 또는 신고수 = 신고수 +1

      -->
      <button v-on:click="신고수[0]++">허위매물신고</button> <span>신고수 : {{ 신고수[0] }}</span>
  </div>
  <div>
      <img alt="" src="./assets/images/room1.jpg" class="room-img"> 
      <h4>{{ products[1] }} 원룸</h4>
      <p>{{ price2 }} 만원</p>
      <button @click="increase">허위매물신고</button> <span>신고수 : {{ 신고수[1] }}</span>
  </div>
  <div>
      <img alt="" src="./assets/images/room2.jpg" class="room-img"> 
      <h4>{{ products[2] }} 원룸</h4>
      <p>{{ price3 }} 만원</p>
      <!-- 
        @mouseover / mouseover를 체크하는 이벤트 핸들러
      -->
      <button @mouseover="신고수[2]++">허위매물신고</button> <span>신고수 : {{ 신고수[2] }}</span>
  </div>

  <hr>

<div>원룸샵4</div>
  <div v-for="(a,i) in 원룸들" :key="i">
      <div>{{ 원룸들[i].id }}</div>
      <!-- 
        - v-bind: 디렉티브는 v-bind를 생략하고 : (콜론)으로 사용 할 수도 있음
        - 속성 안에 데이터 넣을때 속성 앞에 : (콜론) 넣어야 됨 
        :src="원룸들[i].image"
        예시) <img alt="" :src="원룸들[i].image" class="room-img"> 
      -->
      <img alt="" :src="원룸들[i].image" class="room-img"> 
      <h4  @click="모달창열렸니1 = true">{{ 원룸들[i].title }}</h4>
      <p>{{ 원룸들[i].price }}원</p>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'

import apple from './data/oneroom'
apple;

import {apple1,apple2} from './data/oneroom2'
apple1; apple2;

import Post_test from './json/post'

export default {
  name: 'App',
  data(){
    return{
      // 배열 데이터 
      // 저장공간 (리액트에선 state(상태) 라고도 부름)

      모달창열렸니 : false, // false(거짓), true(참)
      모달창열렸니1 : false,
      신고수 : ['0', '0', '0'],
      메뉴들 : ['Home', 'Shop', 'About'],
      가격 :[ 
        {price1 : '50', products1 : '역삼동'},
        {price1 : '60', products1 : '천호동'},
        {price1 : '70', products1 : '마포구'},
        ],
      price1 : 50,
      price2 : 60,
      price3 : 70,
      products : ['역삼동2', '천호동2','마포구2'],
      원룸들 : Post_test, 
    }
  },
  methods :{
    // javascript 함수 만드는 곳
    increase(){
      // 함수 안에 배열 데이터 쓸려면 this. 넣아야함   
      // this.데이터명

      this.신고수[1]++;
    }
  },
  components: {
    //컴포턴트 링크 

    // HelloWorld
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /* margin-top: 60px; */
}

.menu {
  background-color:darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 10px;
  text-decoration: none;
}

.room-img{
  width: 100%;
  margin-top: 40px;
}


body {
  margin : 0;
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%;
  height: 100%;
  background-color: rgba(0,0,0,0.5);
  position: fixed;
  padding: 20px;
}
.white-bg{
  width: 100%;
  background: white;
  border-radius: 8px;
  padding: 20px;
}
</style>
