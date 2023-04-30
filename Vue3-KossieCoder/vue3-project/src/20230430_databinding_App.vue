<template>
  <!-- 단건 테스트 -->
  <input type="text" v-model="name"/>

  <!-- 객체 테스트 -->
  <input type="text" v-model="profile.name"/>
  <input type="text" v-model="profile.id"/>
  <input type="password" v-model="profile.password"/>
  <button class="btn btn-success" @click="onSubmit">Click</button>
</template>

<script>
  // ref : 로 데이터를 바인딩함
  import {ref} from 'vue';
  // import {reactive} from 'vue';
  export default {
    // 화면에 데이터나 이벤트를 그려지게함
    setup() {
      // 단건의 경우
      let name = ref("Kong Mi Hyang");
      
      // 만약 객체로 접근한다면...?
      let profile = {
        name : ref("KONG").value,
        id : ref("MI").value,
        password : ref('HYANG').value,  
      };


      const onSubmit = () => {
        console.log(profile.name);
        console.log(profile.id);
        console.log(profile.password);
      }
    
      
      return {
        name,
        onSubmit,
        profile,
      };
    }
  }
</script>

<style>
  .name {
    color: blue;
  }
</style>