<template>
  <div class='textAreaWithLabel'>
    <label :for='name' class='textAreaWithLabel__label'>{{label}}</label>
    <textarea
      :id='name'
      :class='["textAreaWithLabel__input", {["textAreaWithLabel__input--error"]: maxLength && maxLength < value.length}]'
      :placeholder='placeholder'
      :value='value'
      :type='type' @input='$emit("input", $event.target.value)'
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
      required: false,
      default() {
        return undefined;
      }
    }
  }
});
</script>

<style lang='scss' scoped>
.textAreaWithLabel {
  &__label {
    display: block;
    width: 100%;
    text-align: left;
    font-size: 18px;
    color: #1D2C31;
  }

  &__input {
    height: 120px;
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
