<template>
  <div class="verification">
    <h2>Подтверждение аккаунта</h2>
    <p>Для подтверждения вашего аккаунта вам нужно заполнить все поля,
      подтвердить почтовый ящик и телефон, а также загрузить сканы ваших документов</p>
    <div class="upload">
      <DocumentUpload
        name="file-photo"
        text="Загрузить скан страницы с фотографией"
        successText="Страница с фотографией"/>
      <DocumentUpload
        name="file-registaration"
        text="Страница с пропиской"
        successText="Страница с пропиской"/>
    </div>
  </div>
</template>

<script>
import DocumentUpload from '@/components/DocumentUpload';

export default {
  name: 'AccVerification',
  components: {
    DocumentUpload
  }
}
</script>

<style lang="scss">
  .verification {
    width: 60%;
    margin: 0 auto;

    .upload {
      display: table;
      width: 100%;

      // display: flex;
      // flex-direction: column;
    }
  }
</style>
