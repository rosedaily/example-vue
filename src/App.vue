<template>
  <div class="menu">
    <!-- v-for="작명 in 반복할수"   작명이 보여지는 것은 아니니 아무렇게나 작성. 
    반복할수에 데이터를 넣으면 그 수만큼 반복 {{데이터}} 형태가 아닌 데이터
    :key="" 도 필수로 함께 사용. 에러메시지를 바로 알려줌
    작명으로 채워줘도 된다.  
    <a v-for="a in 메뉴들" :key="a">{{a}}</a> 
    <a v-for="(aa,i) in 메뉴들" :key="i">{{ aa }}</a>  //인덱스 값이 필요한 경우
    -->
    <a v-for="a in 메뉴들" :key="a">{{ a }}</a>  
  </div>
  <!-- v-if="true or false값" -->
  <div class="black-bg" v-if="모달창열렸니">
    <div class="white-bg">
      <h4>상세페이지</h4>
      <p>상세페이지 내용</p>
    </div>
  </div>
    <!-- 
    div를 v-for를 통해 반복
    <div v-for="(a,i) in 메뉴들" :key="a">
      <h4>{{ products[i] }}</h4>
      <p>{{ price[i] }} 만원</p>
    </div> 
  -->
    <!-- 
      v-on:click="자바스크립트" 은 @click="자바스크립트" 으로 축약할 수 있다. 
      자바스크립트 안쪽에 데이터++ 같은 식으로 데이터 값 증감도 가능하고,
      function 도 물론 가능하다! 함수명()이 아닌 함수명
      click외에도 다양한 방법이 있다.
    -->
  <!-- <div>
    <img :src="원룸들[0].image" class="room-img">
    <h4>{{ 원룸들[0].title }}</h4>
    <p>{{ 원룸들[0].price }} </p>
  </div>
  <div>
    <img :src="원룸들[1].image" class="room-img">
    <h4 >{{ 원룸들[1].title }}</h4>
    <p>{{ 원룸들[1].price }} </p>
  </div>
  <div>
    <img :src="원룸들[2].image" class="room-img">
    <h4>{{ 원룸들[2].title }}</h4>
    <p>{{ 원룸들[2].price }} </p>
  </div> -->

  <div v-for="(a,i) in 원룸들" :key="a">
    <img :src="원룸들[i].image" class="room-img">
    <h4 >{{ 원룸들[i].title }}</h4>
    <p>{{ 원룸들[i].price }} </p>
  </div>

</template>

<script>
//{{ 데이터바인딩 하는 이유 }}
//html에 가변적인 데이터는 하드코딩을 하면 추후 변경이 어려움
//Vue의 실시간 자동 렌더링을 사용하기 위해. (웹앱)

import data from './assets/oneroom';

export default {
  name: 'App',
  data(){ //data를 모아두는 공간
    return{
      원룸들 : data,
      모달창열렸니 : false,
      신고수 : [0,0,0],
      메뉴들 : ['Home','Products','about'],
      price : [50,70, 30],
      price1 : 20,
      price2: 50,
      price3 : 70,
      products : ['역삼동원룸', '천호동원룸','마포구원룸']
    }
  },
  methods: {//함수공간
    increase(){
      this.신고수++
    }
  },
  components: {
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
}
body{
  margin: 0;
}
div{
  box-sizing: border-box;
}
.menu{
  background-color: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a{
  color: white;
  padding: 10px;
}
.room-img{
  width: 100%;
  margin-top: 40px;
}
/* 모달창 UI CSS */
.black-bg{
  background-color: black;
  width: 100%;
  height: 100%;
  background-color: rgba(0,0,0,0.5);
  position: fixed; padding: 20px;
}
.white-bg{
  background-color: white;
  border-radius: 8px;
  padding: 20px;
}


</style>
