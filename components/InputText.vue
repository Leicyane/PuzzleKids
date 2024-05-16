<template>
    <div>
      <label>
        <strong>{{title}}</strong>
      </label>
        <input :id="idInput" :type="idInput"  @input="updateValue($event)" />
    </div>
  </template>
  
  <script lang="js">
  import Vue from 'vue'
  
  export default Vue.extend({
    props: {
        title: String,
        idInput: String,
    },
    data() {
      return {}
    },
    methods: {
      updateValue(event) {
        this.$emit('input', event.target.value)
      }
    },
  })
  </script>
  
  <style scoped lang="scss">
  input {
    width: 100%;
    height: 2.5rem;
    padding: 0 0.7rem;
    background: #fff;
    outline: none;
    border: 1px solid #D5E7D9;
    border-radius: 5px;
  }
  
    strong {
      font-size: .7rem;
    }

  </style>
  