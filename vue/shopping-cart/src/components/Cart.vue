<template >
  <div>
    <h2>我是购物车</h2>
    <table>
      <tr>
        <td>勾选</td>
        <td>课程名称</td>
        <td>课程价格</td>
        <td>数量</td>
        <td>总价</td>
      </tr>
      <tr v-for="(item, index) in courseItem" :key="item.id">
        <td>
          <input type="checkbox" v-model="item.isActive" />
        </td>
        <td>{{item.name}}</td>
        <td>{{item.price}}</td>
        <td>
          <button @click="minus(index)">-</button>
          {{item.number}}
          <button @click="add(index)">+</button>
        </td>
        <td>{{item.price*item.number}}</td>
      </tr>
    </table>
  </div>
</template>

<script>
export default {
  props: ["courseItem"],
  methods: {
    add(index) {
      // this.courseItem[index].number += 1;
    },
    minus(index) {
      // this.courseItem[index].number -= 1;
      let number = this.courseItem[index].number;
      if (number > 0) {
          
      }
    }
  }
};
</script>

<style scoped>
</style>