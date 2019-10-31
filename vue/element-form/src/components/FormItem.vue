<template>
  <div>
    <label for>{{label}}</label>
    <div>
      <slot></slot>
      <p v-if="errorStatus">{{errorMsg}}</p>
    </div>
  </div>
</template>

<script>
import Schema from "async-validator";
export default {
  inject: ["kForm"],
  props: ["label", "prop"],
  data() {
    return {
      errorMsg: "",
      errorStatus: false
    };
  },
  mounted() {
    this.$on("validate", this.validator);
  },
  methods: {
    validator() {
      const rules = this.kForm.rules[this.prop];
      const value = this.kForm.model[this.prop];
      const descriptor = { [this.prop]: rules };
      // 描述对象
      const schema = new Schema(descriptor);
      schema.validate({ [this.prop]: value }, errors => {
        if (errors) {
          this.errorMsg = errors[0].message;
          this.errorStatus = true;
        } else {
          this.errorMsg = "";
          this.errorStatus = false;
        }
      });
    }
  }
};
</script>

<style>
</style>