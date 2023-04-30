<template>
  <!-- vue2의 경우 div끼리 묶을 경우 상위에 div가 필요했지만 이제 vue3에서는 나란히 둘 수 있다. -->
  <div class="name">{{ name }}</div>
  <!-- 함수는 이렇게 () 넣어줘야 한다. 매개 변수도 보낼 수 있다. -->
  <!-- <div>{{ greet }}</div> -->
  <!-- v-bind는 : 와 같다. -->
  <input :type="type" :class="nameClass" :value="name"/>
  <button 
    class="btn btn-success"
    @click="updateName"
  >
    Click
  </button>
</template>

<script>
  // ref : 로 데이터를 바인딩함
  import {ref} from 'vue';
  // import {reactive} from 'vue';
  export default {
    // 화면에 데이터나 이벤트를 그려지게함
    setup() {
      let name = ref("Kong Mi Hyang");
      let type = ref("text");
      const nameClass = ref("name");
      // let name = reactive({
      //   id : 1
      // });
      
      // 펑션을 몇 개든 만들어도 된다.
      // const greeting = (name) => {
      //   return 'Hello, ' + name;
      // };

      // const greet = greeting(name);
      // 또 ref로 접근하면 name.value로 값을 가져와야 한다.
      // 아마 콘솔 찍으면 이것저것 있을 것 같다.
      // ref에는 다양한 객체가 들어갈 수 있다.
      // reactive는 오로지 자료만 가져올 수 있다. 이벤트 접근 권한의 차이인 듯
      const updateName = () => {
          name.value = "Kossie";
          // name.id = 2;
      }

      return {
        name,
        type,
        nameClass,
        updateName
      };
    }
  }
</script>

<style>
  .name {
    color: blue;
  }
</style>