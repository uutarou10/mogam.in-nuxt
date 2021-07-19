<template>
  <div class='inputWithLabel'>
    <label :for='name' class='inputWithLabel__label'>{{label}}</label>
    <input
      :id='name'
      :class='["inputWithLabel__input", {["inputWithLabel__input--error"]: maxLength && maxLength < value.length}]'
      :placeholder='placeholder'
      :type='type'
      :value='value'
      @input='$emit("input", $event.target.value)'
    />
  </div>
</template>

<script lang='ts'>
import Vue from 'vue';

export default Vue.extend({
  props: {
    value: {
      type: String,
      required: true
    },
    label: {
      type: String,
      required: true
    },
    name: {
      type: String,
      required: true
    },
    placeholder: {
      type: String,
      required: false,
      default() {
        return "";
      }
    },
    type: {
      type: String,
      required: false,
      default() {
        return "text"
      }
    },
    maxLength: {
      type: Number,
      default() {
        return undefined;
      }
    }
  }
});
</script>

<style lang='scss' scoped>
.inputWithLabel {
  &__label {
    display: block;
    width: 100%;
    text-align: left;
    font-size: 18px;
    color: #1D2C31;
  }

  &__input {
    width: 100%;
    background: #FFF;
    border: 1px solid #AEAEAE;
    border-radius: 4px;
    padding: 12px;
    margin-top: 12px;
    transition: border-color .2s;

    &:focus {
      border-color: #20C0FB;
    }

    &--error {
      border-color: #FE4B26 !important;
    }
  }
}
</style>
