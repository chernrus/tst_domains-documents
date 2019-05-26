<template>
  <div class="verification">
    <h2>Подтверждение аккаунта</h2>
    <p>Для подтверждения вашего аккаунта вам нужно заполнить все поля,
      подтвердить почтовый ящик и телефон, а также загрузить сканы ваших документов</p>
    <div class="upload">
      <div class="upload__document ">
        <div class="upload__document-image">
          <ImageUploadStatus v-bind:imgType="status"/>
        </div>
        <div class="upload__document-file">
          <input type="file" name="file-photo" id="file-photo">
          <label for="file-photo">Загрузить скан страницы с фотографией</label>
          <p>Размер файла не более 5Мб</p>
        </div>
        <div class="upload__document-status">
          Идет проверка
        </div>
      </div>
      <div class="upload__document">
        <div class="upload__document-image">
          <ImageUploadStatus v-bind:imgType="status"/>
        </div>
        <div class="upload__document-file">
          <input type="file" name="file-registaration" id="file-registaration">
          <label for="file-registaration">Страница с пропиской</label>
          <p>Размер файла не более 5Мб</p>
        </div>
        <div class="upload__document-status">
          Идет проверка
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import ImageUploadStatus from '@/components/ImageUploadStatus';

export default {
  name: 'AccVerification',
  components: {
    ImageUploadStatus
  },
  data() {
    return {
      status: 'upload'
    }
  },
  methods: {
    getImgUrl(pic){
      return require(`@/assets/img/${pic}.svg`);
    }
  }
}
</script>

<style lang="scss">
  .upload {
    display: table;

    &__document {
      display: table-row;

      div {
        display: table-cell;
      }

      &-file {
        input[type="file"] {
          z-index: -1;
          opacity: 0;
          width: 0;
          height: 0;
          overflow: hidden;
          position: absolute;
        }

        label {
          cursor: pointer;
          text-decoration: underline;
        }
      }
    }
  }
</style>
