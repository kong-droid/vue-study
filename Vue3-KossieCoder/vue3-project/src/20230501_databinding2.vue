<template>
  <!-- 
    v-show, v-if 차이점
    v-show : 초반에 모두 랜더링 해와서 처음 속도는 느리지만 이후에 빠름
    v-if : 조건문에 따라 랜더링 해오고 바뀔 때 마다 랜더링 하기 때문에 이후엔 느림
    상황에 맞게 사용하면 좋을 것 같다.
  -->
  <!-- <div v-show="toggle">true</div>
  <div v-show="!toggle">false</div> -->
  <div v-if="toggle">true</div>
  <div v-else>false</div>
  <button
    @click="onToggle"
    class="btn btn-primary" 
  >
    click me!
  </button>
  <div class="container">
    <h1>To-do List</h1>
    <!-- form은 제출이 되면 자동으로 리프레시를 한다. 
        방지 방법은 event를 통해 제어한다.
        ex ) e.preventDefault();
        ex ) submit.prevent
    -->
    <form class="d-flex" @submit.prevent="onSubmit">
      <div>
        <div class="flex-grow-1 mr-2">
          <input 
            type="text" 
            v-model="toDo.what" 
            class="form-control"
            placeholder="type new To-do!"
          />          
          <input 
            type="text" 
            v-model="toDo.name" 
            class="form-control"
            placeholder="what's your name?"
          />
        </div>
        <div>
          <button 
            class="btn btn-success" 
            type="submit"
          >
            Add
          </button>
        </div>
        <div v-if="hasError" style="color: red;">this is field cannot be empty!</div>
      </div>
    </form>
    <!-- {{toDos}} -->
    <!-- :key값은 각각의 노드의 위치를 파악하기 위해 사용한다.-->
    <div 
      class="card mt-2" 
      v-for="doIt in toDos" 
      :key="doIt.what">
      <div  class="card-body p-2">
        {{"오늘 해야할 일 : \t" + doIt.what + "\t ," + "작성자 : \t" + doIt.name}}
      </div>
    </div>
  </div>
</template>

<script>
  // ref : 로 데이터를 바인딩함
  import {ref} from 'vue';
  // import {reactive} from 'vue';
  export default {
    // 화면에 데이터나 이벤트를 그려지게함
    setup() {
      const toggle = ref(false);
      
      const hasError = ref(false);

      // 만약 객체로 접근한다면...?
      const toDo = ref({
        what : '',
        name : ''
      });
    
      const toDos = ref([
        {what : 'Vue 공부', name: '공미향'},
        {what : 'JPA 공부', name: '공미향'},
        {what : 'Android 공부', name: '공미향'},
        {what : 'React 공부', name: '공미향'},
        {what : '소프트웨어 공학 공부', name: '공미향'},
      ]);

      const onSubmit = () => {
        // e.preventDefault();
        if(toDo.value.what === '') {
          hasError.value = true;
        } else {
          hasError.value = false;
          toDos.value.push(toDo.value);
        }
      }
      
      const onToggle = () => {
        toggle.value = !toggle.value;
      };

      

      return {
        toDo, 
        toDos,
        onSubmit,
        toggle,
        onToggle,
        hasError
      };
    }
  }
</script>