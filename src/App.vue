<template>
  <div class="form">
    <div class="form-group">
      <label for="dropdown">Select an option</label>
      <Dropdown :data="data" v-model="formData.dropdown" placeholder="Select an option"/>
    </div>
    <div class="form-group">
      <label for="dropdown">Select multiple option</label>
      <Dropdown :data="data" :multiple="true" v-model="formData.dropdownMultiple" placeholder="Select multiple option"/>
    </div>
    <div class="formdata">
        <code class="formdata-content">
          <pre>formData:{{ JSON.stringify(formData, null, 2) }}</pre>
        </code>
    </div>
  </div>
</template>

<script>
import Dropdown from './components/Dropdown/Dropdown.vue';

export default {
  name: 'App',
  components: {
    Dropdown
  },
  data(){
    return{
      data: [
        {
          id: 1,
          name: 'Option 1'
        },
        {
          id: 2,
          name: 'Option 2'
        },
        {
          id: 3,
          name: 'Option 3'
        },
        {
          id: 4,
          name: 'Option 4'
        },
        {
          id: 5,
          name: 'Option 5'
        },
        {
          id: 6,
          name: 'Option 6'
        },
        {
          id: 7,
          name: 'Option 7'
        },
      ],
      formData: {
        dropdown: '',
        dropdownMultiple: []
      }
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.form{
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
  text-align: left;
}
.form-group{
  margin-bottom: 20px;
}
.formdata{
  margin-top: 20px;
  background-color: #000;
  width: 300px;
  color:'#fff';
  color: #fff;
  padding: 10px 20px;
  border-radius: 5px;
  font-size: 14px;
  font-family: 'Courier New', Courier, monospace;
  min-height: 100px;
  max-height: 150px;
  overflow-y: scroll; 
  &::-webkit-scrollbar {
      width: 5px;
  }
  &::-webkit-scrollbar-track {
      background: #f1f1f1;
  }
  &::-webkit-scrollbar-thumb {
      background: #888;
      border-radius: 5px;
  }
  &::-webkit-scrollbar-thumb:hover {
      background: #555;
  }
}

</style>

