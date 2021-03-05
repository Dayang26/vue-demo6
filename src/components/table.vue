<template>
  <div id="app">
    <p>欢迎：{{ user }}</p>
    <div>
      <table id="table">
        <tr>
          <th>Name</th>
          <th>Age</th>
          <th>Grade</th>
          <th>Edit</th>
          <th></th>
          <th></th>
        </tr>
        <tr v-for="(data2, idx) in data1" :key="idx">
          <td v-for="data3 in data2">{{ data3 }}</td>
          <td><button type="button" @click="del(idx)">Delete</button></td>
          <td><button type="button" @click="fix(idx)">Fix</button></td>
          <td><button type="button" @click="Add">Add</button></td>
        </tr>
      </table>
    </div>

    <div id="add" v-if="show">
      <h4>Name:</h4>
      <input type="text" :value="name"  placeholder="edit me"/>

      <h4>Age:</h4>
      <input type="text" v-model="age" />

      <h4>Grade:</h4>
      <input type="text" v-model="grade" />

      <button @click="push()">over</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'table',
  props: {
    user: {
      type: String,
      default: 'Laura'
    }
  },
  data() {
    return {

      show: true,
      name: '',
      age: '',
      grade: '',

      data1: [{ name: '123', age: '12', grade: '123' }, { name: '123', age: '12', grade: '123' }],
      data2: { name: '', age: '', grade: '' }
    };
  },
  methods: {
    Add() {
      this.show = !this.show;
    },
    push() {
      console.log(this.name), console.log(this.age), console.log(this.grade), console.log(this.show);
      var a = this.name;
      var b = this.age;
      var c = this.grade;
      Object.defineProperty(this.data2, 'name', { value: a });
      Object.defineProperty(this.data2, 'age', { value: b });
      Object.defineProperty(this.data2, 'grade', { value: c });

      console.log(this.data2);
      this.data1.push(this.data2);
    },
    del(idx) {
      this.data1.splice(idx, 1);
    },
    fix(idx) {}
  }
};
</script>

<style>
table,
td,
th {
  border: 1px solid black;
}

table {
  width: 100%;
  border-collapse: collapse;
}
</style>
