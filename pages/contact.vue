<template>
  <div>
    <AppHeading :level='1' class='pageTitle'>Contact</AppHeading>
    <p>
      ご連絡は以下のフォームまたは
      <a href='https://twitter.com/mogamin3' target='_blank'>Twitter</a>
      のダイレクトメッセージよりお願いいたします。
    </p>
    <form class='contactForm' @submit.prevent='submit'>
      <InputWithLabel v-model.trim='name' name='name' label='お名前' />
      <InputWithLabel v-model.trim='email' value='' name='email' label='メールアドレス' type='email' />
      <TextAreaWithLabel v-model.trim='body' value='' name='body' label='本文(400字まで)' :max-length='400' />
      <div class='contactForm__submit'>
        <FormButton class='contactForm_button' type='submit' :disabled='isDisabled'>
          {{isSending ? "送信中..." : "送信"}}
        </FormButton>
      </div>
    </form>
  </div>
</template>

<script>
import axios from 'axios';
import AppHeading from '../components/AppHeading'
import InputWithLabel from '../components/InputWithLabel'
import TextAreaWithLabel from '../components/TextAreaWithLabel'
import FormButton from '../components/FormButton'

const emailRegex = /[\w\-._]+@[\w\-._]+\.[A-Za-z]+/;

export default {
  components: { FormButton, TextAreaWithLabel, InputWithLabel, AppHeading },
  data() {
    return {
      name: '',
      email: '',
      body: '',
      isSending: false
    }
  },
  head: {
    title: 'Contact'
  },
  computed: {
    isDisabled() {
      return this.isSending || this.name.length === 0 || this.email.length === 0 || this.body.length === 0 || this.body.length > 400 || !emailRegex.test(this.email);
    }
  },
  methods: {
    async submit() {
      this.isSending = true;
      try {
        await axios.post(
          'https://us-central1-mogamin-playground.cloudfunctions.net/sendContact',
          {name: this.name, email: this.email, content: this.body}
        );
        alert(
          '送信しました。返信が必要と判断したものに関してはこちらよりご連絡いたします。'
        );
        this.resetForm();
      } catch {
        alert('申し訳ありません。送信できませんでした。\n再度お試しください。');
      } finally {
        this.isSending = false;
      }
    },
    resetForm() {
      this.name = "";
      this.email = "";
      this.body = "";
    }
  }
}
</script>

<style lang='scss' scoped>
.pageTitle {
  margin-bottom: 64px;
}

.contactForm {
  display: grid;
  gap: 32px;
  margin-top: 32px;
   &__submit {
     display: flex;
     justify-content: center;
     width: 100%;
   }
}
</style>
